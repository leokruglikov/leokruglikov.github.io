---
title: "ROOT histograms & Poisson distribution"
date: "2023-02-21T22:33:44+01:00"
draft: false
tags: ["tutorial", "physics"]
katex: true
markup: "mmark" 
---

![](/images/root_hist_poisson.jpg)


### The radioactive experiment
The Poisson distribution occurs quite often in particle physics. For example, we consider 
a sample of Cesium 137. It is radioactive, emitting photons and electrons, and its half-life is very significant ($\approx 30$ years). 
From this fact, it is wise to suppose that the rate, at which the radioactive products are emitted con be considered constant within the 
timeframe of the conducted experiment.

The experiment consists of a radioactive source (Cesium 137) and a Photo-detector. The data to be obtained are the number of collision per certain time interval.
That is, some observation time $T$ will be taken and divided into a time interval (3 types of this time 
time intervals - t=\{1, 10, 100\}, [ms]). The goal is to measure the number of emitted photons per one time interval t during this long observation time T. 
It is clear that in average, the number of emitted photons $\gamma$ will be greater for the time interval t=100ms than t=1ms.

### The Poisson distribution
The fact is that the probability/rate, at which these photons will be emitted during this T>>t, will be following a Poisson distribution. Lets recall the idea 
behind the Poisson distribution. It expresses the _likelihood_ and probability distribution that some event of probability p will occur after some time. For example, suppose in 
a call center, there is in average one call per some period of time tau. This does not mean that the call will be certainly received after time tau (after e.g. the beginning of 
the workday). Instead, there is some probability distribution with mean tau. This call-center situation is similar to the problem of radioactivity, where calls can be mapped to Gamma 
emissions.
The Poisson distribution is a discrete PMF and has the form of $$ f(n) = \dfrac{e^{-\lambda}\lambda^{n}}{n!}$$ We can also write it with some multiplicative constant, 
as we will record $\gamma$ and their numbers, not their probability (we can of course normalize them if needed):
$$ f(n) = A\dfrac{e^{-\lambda}\lambda^{n}}{n!}$$

### ROOT for fitting the Poisson distribution
We will use the ROOT library to process the number of events recorded in this simple experiment, as done in CERN. We will write a full program (i.e. not a ROOT script) and compile it with `g++`.

We will start with reading the data 
```C++
#include <fstream>
#include <vector>
#include <string>
std::vector<std::vector<double> read_data(){
  std::vector<std::string> fnames {"1ms.dat", "10ms.dat", "100ms.dat"};
  std::vector<std::vector<double> data;
  for(auto fname: fnames){
    std::fstream file;
    file.open(fname.c_str(), std::ios_base::in);
    std::vector<double> from_file; double temp=0.0;
    while(file>>temp){
      from_file.push_back(temp);
    }
    data.push_back(std::move(from_file));
  }
  return data;
}
```

Then, we will start to create histograms: 
```C++
#include "TH1.h"
#include "TF1.h"
//function returning a vector (will be of size 3) of pointers to ROOT histograms
std::vector<TH1D*> create_hists(const std::vector<std::vector<double>& data){
  //we will record the maximum and minimum for each experiment,
  //in order to construct the histograms
  std::vector<std::pair<double, double>> min_max;
  for(d : data){
    double min = *std::min_element(d.begin(), d.end());
    double max = *std::max_element(d.begin(), d.end());
    min_max.push_back({min, max});
  }
  
  //we can possibly experiment with different number of bins
  int n_of_bins = 30;
  std::vector<TH1D*> hists;
  for(int i = 0; i<data.size(); i++){
    hists.push_back(new TH1("", "", n_of_bins, min_max[i].first, min_max[i].second));
  }
  for(int i = 0; i<data.size(); i++){
    for(int j = 0; j<data[i].size(); j++){
      hists[i]->Fill(data[i][j]);
    }
  }
  
  return hists;
}
```
Okey, now, if we draw, e.g a histogram using `hists[i]->Draw()`, we will obtain the histogram (after some styling using the `View->Editor` tab 
& clicking the necessary part to style) that resembles that:
|![](/images/root_witout_fit.jpg)|![](/images/root_witout_fit_second.jpg)|
|:--:|:--:| 
| *Histogram for the 1ms* | *Histogram for the 10ms*|

|![](/images/root_witout_fit_third.jpg)|
|:--:|
|*Histogram for 100ms*|
> These are 3 histograms that I obtained from the data of the experiment


Now, we're interested in how to fit these. There is apparently no ready-to-use Poisson distribution as for the Gaussian 
(in order to fit a Gaussian, we would use `hists[i]->Fit("gaus")`). Therefore, we need to create a separate function object.

```C++
void fit(std::vector<TH1D*> hists,std::vector<std::pair<double,double>> min_max, \\
        int which_fit, std::string func_name="f"){

    //create a function object with the corresponding 
    //formula that we need to fit (in our case, "continious" Poisson)
    //The parameters to be fitted are indicated in [].
    //Those will be the ones that we want to obtain at the end of the fit 
    //and those are the ones that will fully gouvern our Poisson distribution
    //In this case, [0]=A and [1]=lambda as in the formula
    TF1* to_fit = new TF1(func_name.c_str(), \\
      "[0]*TMath::Exp([1])*(TMath::Power([1], x))/(TMath::Gamma(x+1))",\\
      min_max[which_fit].first, min_max[which_fit].second);

    //how many (discrete) points will the func have
    int f_points = 1000;
    to_fit->SetNpx(f_points);

    //We set all the parameters of the function 
    //to some initial value (different from 0), 
    //so that the process of minimization (fitting) can start from "somewhere"
    to_fit->SetParameters(1,1);

    //We will finally fit the histogram by the function 
    //that we identify by its name
    //we also pass the parameters 
    //(M and E for better fitting and R for using the range 
    //specified in the function itself (in our case, [min, max])
    hists[which_fit]->Fit(func_name.c_str(), "MER");

    //for drawing if not done before
    //hists[which_fit]->Draw()
}
```
This code will therefore try to fit using the embedded in ROOT minimization strategies. The output of the minimization 
will print information to the console (if not specified otherwise). The end of the output should look something like this 
(do not pay attention to the numbers).

```TXT
FCN=63.5219 FROM MINOS     STATUS=SUCCESSFUL     14 CALLS         116 TOTAL
                     EDM=6.20703e-11    STRATEGY= 1      ERROR MATRIX ACCURATE 
  EXT PARAMETER                                   STEP         FIRST   
  NO.   NAME      VALUE            ERROR          SIZE      DERIVATIVE 
   1  p0           1.49633e+04   3.36157e+02  -7.48335e+00   7.84651e-08
   2  p1           1.88856e+03   8.63491e-01   8.63491e-01  -2.53964e-05
```
If the fitting (minimization) process has been successful, we will see `STATUS=SUCCESSFUL`. 
If not, there can be different types of outputs, depending on what went wrong during the 
optimization. An example of a unsuccessful result is `STATUS=FAILED` together with a message 
of the type `Warning in <Fit>: Abnormal termination of minimization.`.

The output shows the value of the fitted parameters. In the output, in our case, $A is in fact `[0]` and is equal to `p0`, and 
lambda is equal to `[1]` is equal to `p1`. In the output, we also have the errors of the parameters, which can also be very useful 
to determine, whether the fit is trustworthy.

### Possible caveats

In our case, we have 3 sets of data. We can clearly see that they are quite different. The computed averages are $\approx 19$, $\approx 190$ 
and $\approx 1900$. This means that, the order of magnitude for different datasets differ. That means, that during the minimization 
process, ROOT will _need to go to the 190's_ for the 10ms dataset and to the 1900's for the 100ms dataset.

What I mean here is that during the minimization process, the function will be evaluated at x's of that order. The function that should 
be fitted here is composed of Gamma(x) function, as well as lambda^x, which is a power function. Therefore, when we will evaluate it, 
we will have the terms of order `Gamma(1000) = 1000!` and $$\mathbb{E}^{1000} \approx 1000^{1000}$$, as $$\mathbb{E}=\lambda$$.
These are huge numbers and cannot be represented fully on a _normal_ system wihtout using extended libraries for big numbers, as the 
numbers will overflow (if the fitting for x's of this orders is done in Python, a warning will be shown).
For the data given here, I personally do not have problems for the first dataset for 100ms. The data is correctly fitted without any problems.
The resulting fitted parameters are pretty accurate and the obtained value of the principal parameter $\lambda$ being the mean and the variance of 
the Poisson distribution: $$\lambda = \mathbb{E}=\text{Var}$$.

For the next datasets (10ms and 100ms). There is, however, a problem occuring. The minimization simply fails, without specifying any particular 
reason. We can then suppose that this is due to the fact that the function involved in the distribution overflow for big values of x's.

The possible solution to this problem can be for example normalizing the bins and shifting them to zero. Normalizing the bins is indeed a good idea, 
to limit the value of $A$ to around $1$. For the problem of evaluating for greater x's, this would probably be the solution for the data of 10ms, but 
not for the 100ms. Indeed, we see that the range in x's (range$\equiv$min$-$max) in the 1ms is around $30$. For the 10ms data, the range is 
around 80 and for 100ms, it is around 250. This means that even when shifted, our complex `Gamma(x)` values will be evaluated at great x's of 
order of `x\approx 150`. Therefore, this is not a great solution, especially if there are greater dataset (e.g. potentially 1000ms).

Another solution (the one used to fit here) is the result known as the **Stirling approximation**. What this theorem says is that 
the factorial (thus the \Gamma(x) function, which is the equivalent of a factorial for real numbers) can be approximatied as follows:
$$ x!=\Gamma(x+1) \sim \sqrt{2\pi x}\biggl( \dfrac{x}{e} \biggr)^x$$

We can further develop this expression for the Poisson distribution:
$$f(x)=A \dfrac{e^{-\lambda} \lambda^x}{\Gamma (x+1)} \xrightarrow{\Gamma(x+1)\sim \text{...}}A \dfrac{e^{-\lambda} \lambda^x}{\sqrt{2\pi x}\biggl( \dfrac{x}{e} \biggr)^x} $$
We also the use the fact that we can write any exponent as $$a^b = e^{a\ln(b)}$$, thus, 
$$A \dfrac{ e^{-\lambda} e^{x \ln(\lambda)} e^{x}}{\sqrt{2\pi x x^x}} = A\dfrac{ e^{-\lambda} e^{x \ln(\lambda)} e^{x}x^{-x}}{\sqrt{2\pi x}} = A\dfrac{ e^{-\lambda} e^{x \ln(\lambda)} e^{x}e^{-x\ln(x)}}{\sqrt{2\pi x}} = A\dfrac{ e^{-\lambda+x \ln(\lambda)+x-x\ln(x)}}{\sqrt{2\pi x}}$$

This result has an exponential of a sum $$ -\lambda + x\ln(\lambda)+x-x\ln(x) $$ 
where lambda is of the order of x, thus $$-\lambda + x \sim 0$$ (that is, a small order of magnitude). The same argument can be used for $$x\ln(\lambda)-x\ln(x) \sim 0$$.
Thus, there are no big numbers in the exponent and the argument of the exponential does not have function that _"blow up"_ for large numbers. 

This means that we solved our problem of huge number overflow. 
The fitting results of the ROOT using this method give a $\lambda$ **very very** similar to the actual $$\lambda = \mathbb{E}$$. This 
shows that this method is a very good approximation.

|![](/images/root_with_fit_second.jpg)|![](/images/root_with_fit_third.jpg)|
|:--:|:--:| 
| *Histogram for the 10ms with fit and shown parameters* | *Histogram for the 100ms with fit and shown parameters*|





















