---
title: "Cuda Notes"
date: "2023-02-22T22:33:44+01:00"
draft: true
author : "Leo Kruglikov"
cover: "img/cuda_code.jpg"
description : "Self-made notes on programming paradigm with CUDA"
tags: ["notes", "tutorial"]
showReadingTime: true
toc: true
---


GPGPU programming is quite a promising field, involved in different applications. In majority, they are more _science related_, such as, linear algebra (matrix and tensor operations). Many of these packages 
are already successfully implemented in _ready-to-use_ libraries. 

I started to study GPGPU programming on my own. And due to the fact that, in my opinion, the CUDA programming is poorly documented (i.e. videos, tutorials, books), I decided then to write 
my personal notes on this topic. These notes include in fact a significant number of information from different sources, such as books, online tutorials, NVidia's official documentation and blogs.

> Notes are available on my [Github repository](https://github.com/leokruglikov/CUDA-notes), together with the LaTeX sources 
> and the `.pdf` [file](https://github.com/leokruglikov/CUDA-notes/blob/main/cuda_recap.pdf). 
> They are also available here, at the [end of the document](#the-full-pdf)


## Topics covered
- Introduction
- Basics of Architecture
- Programming in CUDA
  - Basic setup on Linux
  - Threads & blocks
  - Memory model
- Basic algorithms & patterns
  - Reduce
- CUDA synchronization
- Introduction to programming tools

## Notes extract
### 4. CUDA synchronization mechanisms
As we've discussed in the section on architecture, when writing kernels,
we always need to think about the GPU's hardware, scheduling, etc\... By
now, with the basic examples we've considered only *basic* operations.
Indeed, the only API function to synchronize execution, that we've used
in the kernel is the `__syncthreads()`. This is a simple syncing
mechanism, that ensures that all the threads **within the block** are
done before this function invocation.

#### Cooperative Groups

{{< code >}}
__device__ int reduce_sum(
    cooperative_groups::thread_group gr, \
                        int *temp, int val){
    int lane = g.thread_rank();

    for (int i = g.size() / 2; i > 0; i /= 2){ 
//map each element in the first "semi" block 
//to it's corresponding element in the second one
        temp[lane] = val;
        g.sync(); // wait for all threads to store
        if(lane<i) val += temp[lane + i];
        g.sync(); // wait for all threads in to load
    }
    return val; //only thread 0 will return full sum
}
{{</ code >}}

*Cooperative groups* is a relatively new feature to the CUDA API. As the
name suggests it, this feature enables us to group threads, with the
ability to perform common, collective operations (or simply
collectives). We can also perform synchronization between the threads,
belonging to the same cooperative groups. With these API features, one
can simplify the code, thus avoiding common mistakes and making it more
readable. For example, in the code snippet above, 
we perform the exact same algorithm as
in the section on reduce algorithm, by using some utility of the CUDA
API. In this case, the `cooperative_groups::thread_group` class (do not
pay attention to how we created this object and/or how it is declared).
The `thread_rank()` function gets the ID/rank of the thread within the
thread group `g` (the same way as `threadId.x` within a block). Then
we're calling the `sync()` function, which ensures that all the threads
within the thread group will be done setting the `val`, and the second
to ensure that all threads are done reducing. It is important to
understand, that all the threads will return the val. However, only the
thread 0 will accumulate all the `val`'s **[10]**.

#### Thread blocks 

We've already seen the notion of a thread block many times. This notion
was always quite *abstract* and implicit. Indeed, while launching the
kernel, we've always kept the notion of thread blocks in our mind, but
never actually accessed it explicitly. However, in newly introduced
features, we can \"access\" the thread block explicitly. Remember the
legacy `__syncthreads()` function. Well, syncing the
`this_thread_block()` does the same thing as the `__syncthreads()`.
Thus, there are several ways/semantics to synchronize the threads. The
following function calls are synonyms.

```C++
    auto tb = this_thread_block(); // gets the thread block in kernel
    tb.sync() // same method as in cooperative_groups
    cooperative_groups::synchronize(tb);
    this_thread_block().synchronize();
    cooperative_groups::synchronize(this_thread_block());
```

One can also mention other synonyms `dim3 threadIdx` $\equiv$
`dim3 thread_index()` and `dim3 blockIdx` $\equiv$ `dim3 group_index()`.
Thus one can easily replace these built-in keywords with these new
methods, without any noticeable performance issues.

#### Partitioning 

For these cooperative groups, a partitioning feature is also available.
For instance, if we've created a thread thread block, by invoking
`auto tb = this_thread_block()`, one can divide it into more small
parts, for instance, into groups of 16 threads. This is done using the
`cooperative_groups::partition()`, method, which takes the subject
itself (the one to be partitioned into groups) and the number of threads
per group. For instance, `cooperative_groups::partition(tb, 16)` divides
the thread block into groups of 16 threads (so if e.g. a block has a max
of 64 threads, this function will create) 4 groups of 16 threads in
each.

The object returned is a `thread_group`. By accessing this object, it is
possible to get the thread's rank, **within the obtained thread_group**
(for instance, if we divide the thread block into groups of 16 threads
and, by passing this object to a device function, print the
`thread_rank()`, method, we will see numbers varying from 0 to 15).

The utility of these features overall is to reduce the errors in code.
Indeed, the NVidia documentation states that the usage of these features
significantly reduces the risk of deadlocks. The concept of deadlocks is
probably well-known to the reader. This is a typical situation when we
don't want different threads to access a critical section, and ask them
to be synchronized before accessing them. Consider the two pieces of
code:

```C++
__device__ int sum(int *x, int n) 
{   ...
    __syncthreads();
    ...
}
__global__ void parallel_kernel(float *x, int n)
{
    if (threadIdx.x < blockDim.x / 2){
        sum(x, count);  // Half of the threads enter and 
                        //the other half-not
    }                   
}
```

```C++
__device__ int sum(thread_block block, int *x, int n) 
{   ...
    block.sync();
    ...
}
__global__ void parallel_kernel(float *x, int n)
{
    sum(this_thread_block(), x, count); //OK
}
```

We clearly see a deadlock in the first piece of code, as there are only
threads with ID's less than the half of the block dimension, which will
enter the `if` condition. Those threads will perform their piece of code
independently and then will wait for all the other threads in the block
to be completed and synchronized. This is a big issue, as there are
threads, which will never start the `sum()` kernel and will just sit up
there, waiting for those, who have. So the two chunks of threads will
just sit and wait for each other infinitely.

This is why one may find an application for the previously discussed
primitives. In the second piece of code, one call the method `sum()`
with a thread block. However, we could have divided it into groups,
using the CUDA functionality discussed above, **and only synchronize
that block**, which, we are sure, will be run by all threads in the
block.

#### Warp synchronizations 

While programing with CUDA, one never gets tired to think about warps,
and how to optimize their execution. I do agree that it is not an easy
task, to think of it while doing even some basic operations. The new
NVidia architectures and new versions of the CUDA API, provides a simple
way to navigate through these concepts.

We have discussed a lot of the advantages of shared memory (e.g. for the
speed and efficiency of the reduce algorithm). However, the new
utilities give us a faster, or even more local way to perform some
operations. Remember, shared memory is block-local memory. Remember also
that every thread has some kind of register to store small intermediate
values while performing a kernel, for example, when we used to store the
local thread ID. The so-called *warp level synchronization primitives*
allow us to access a certain thread's local register from an-another
thread, [as long as they are in the same warp]{.underline}, without the
usage of the shared memory. Again, there are many things to keep in
mind, but if such a function is called, it is doing everything
*atomically*, in the sense that it is a primitive operation, performed
locally on the threads in the warp. We therefore introduce here the
notion of the **lane** (in fact, we used it briefly above). A lane is
the thread id within the warp.

##### A little disclaimer: 

There are various Warp-level primitive functions. We will note that many
function's names are similar, and only differ by the postfix `_sync()`.
For instance, `__shfl_xor()` and `__shfl_xor_sync()` **[3]**,
**[7]**. Indeed, the ones with the `_sync()` postfix are an
improvement of the former. It is recommended to use the newer version
instead. I will not go into great detail about these differences. I will
just mention that there are differences in parameters [^18](see further
examples).

The `__activemask()` primitive/function is actually not a
synchronization mechanism, but more of filtering mechanisms. This
function returns the *indices* of the active threads in the warp, where
it was referenced from[^19]. So the result returned from the
`__activemask()` is used to call other synchronization functions, to
*give them the corresponding threads, that are active in the warp*. So,
for example, one could call the `__syncwarp(MASK)`, thus asking to sync
all the threads meeting the `__activemask()` condition. One can go to
the NVidia's developer's guide **[2]** and find the following:

> *Returns a 32-bit integer mask of all currently active threads in the
> calling warp. The Nth bit is set if the Nth lane in the warp is active
> when \_\_activemask() is called. Inactive threads are represented by 0
> bits in the returned mask.*

So let's have a quick look and example of what did NVidia provide us
with [^20]

-   `__shfl_sync()`, or, in previous CUDA versions, `__shfl()` is a
    tool, to \"broadcast\", or \"spread\" a certain value from a certain
    thread (identified with its lane) to all others in the warp. For
    example, in a certain warp, all the threads have a variable
    `int b = //some random int`, unique for all the threads. And I want
    all these thread's variable `b`, to be the same as the one in the
    thread 4 (its lane number or ID within the warp). The best way to do
    that is to use the provided function:
    `__shfl_sync(0xffffffff, b, 4)` (or `__shfl(b,4)`). The second
    parameter is the variable to be broadcasted and the third one is the
    lane number to take the value from (because, of course, all the
    threads have this local variable `b`, which is different for all of
    them). So we're replacing all the b's with THE b of the thread 4.
    The first parameter is actually the mask/filter, that tells the
    processor (or core I should say) which threads will be involved in
    this operation. This can be used by passing the result of e.g.
    `__activemask()` function (there are multiple *filtering* functions)
    or by passing it the *default* value in hex notation, which
    corresponds to the maximum number that can be displayed in binary
    notation (all the 32 bits are 1, thus we're saying that all the
    threads are active).

-   `__shfl_up_sync()` or in previous CUDA versions `__shfl_up()` is a
    function to shift the values of the warp by an offset. For instance,
    let's say that in the warp, I want the 4'rd thread to have the value
    from 0'th thread, the 5'th thread the value of the 1'st, the 6'th
    thread the value from the 2'nd thread, etc \... Then we would want
    to use the `__shfl_up_sync()` function, with the same parameters as
    in the `__shfl_sync()` function described above.

-   `__shfl_down_sync()` Is the same idea as the `__shfl_up_sync()`. The
    difference is that we would use it if we wanted e.g. the thread 29
    to have the value 31. (see figure for better understanding).

These primitives come in various shapes and forms. It would take quite a
time to discuss them all here. The idea for them all, however, follows
quite well the patterns, we've discussed just above. It is important to
understand that these operations are sort of atomic, because, as we've
seen, these are warp-local primitives, which is the most fundamental
part of the execution scheduling model.

### The full pdf

{{<embed-pdf url="cuda_recap.pdf" hideLoader="true">}}


> [10] Cooperative groups: Flexible cuda thread programming, Aug 2020. URL: [https://developer.nvidia.com/blog/cooperative-groups/](https://developer.nvidia.com/blog/cooperative-groups/).
>
> [3] Cuda shfl xor shfl shfl up() shfl down(). URL: [https://blog.csdn.net/jqw11/article/details/103071556](https://blog.csdn.net/jqw11/article/details/103071556).
> 
>[7] Kepler’s shuffle (shfl): Tips and tricks — gtc 2013.
[http://on-demand.gputechconf.com/gtc/2013/presentations/S3174-Kepler-Shuffle-Tips-Tricks.pdf](http://on-demand.gputechconf.com/gtc/2013/presentations/S3174-Kepler-Shuffle-Tips-Tricks.pdf).
>
>[2] Cuda c++ programming guide. URL: [https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#programming-model](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#programming-model).
