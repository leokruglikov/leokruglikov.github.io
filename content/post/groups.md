---
title: "Applications of group representation theory"
date: "2023-05-17T22:33:44+01:00"
draft: false
tags: ["physics", "notes"]
katex: true
math: true
markup: "mmark" 
showReadingTime: true
toc: true
---


## What is a group?
A group is a ~~very~~ abstract mathematical concept that I like to thing of as an extension to 
the notion of a **set**. That is, a set is quite an abstract mathematical concept. A set is an object that 
"groups" any elements by its properties, or even using any "logic" 
we can think of. 

One can define a set to be, for example, all people of age 32. 
Mathematically, one can define a set of all real numbers, a set of all even numbers, a set of even functions, etc...
A set can be finite, countably infinite, uncountably infinite, etc...
A set can be caracterized by different things, for example 
the cardinality of the set. The cardinality can be thought of as 
the size of the set.

Now, what is a group then?
What the notion of the group does, is it establishes a relationship between the elements in the set. 
Namely, the set simply _"contains"_ elements in an abstract manner. The group, however,
establishes some _"action/connection"_ between the 
contained elements inside this group.

That is, one can for example 
define the addition relationship (e.g. 2 real numbers can be added),
multiplication relationship (e.g. 2 matrices can be multiplied),  composition relationship (e.g. 2 functions can be composed) etc... 
That is, the relationship we're talking about is nothing but a function 
that takes two elements of the set and _spits_ another. 
One can remember that the notion of groups is often backed up by 
examples from symmetries, which are nothing but functions.

An important property of a group is that **all elements in this set can be obtained via each other**. Mathematically speaking, one calls this property "closure". 
> What it means is that for any 2 elements of the group, their 
> product/operation will result in another element of the group.
> Alternatively, any element of the group can be obtained via 
> a binary operation between two elements of the group.

A group is thus an abstract mathematical concept that is based on 2 notions: a set and a binary function. 
The function in the context of a group is called an operation. This operation maps two elements of a set to another 
element of this set. Therefore, a group is a set, with a defined operation (the operation can, e.g. be addition, product, 
composition,...) that we sometimes note as $(G, \circ)$, where $G$ is the set and the $\circ$ corresponds to the binary operation.

>The group $(G, \cdot)$ is said to be a group if it obeys 3 conditions:
>- $\exists!\;e \in G: \forall g \in G, g\circ e = g = e \circ g \quad$. In other words, there exists a neutral element, such that composed with 
>any element in the group, it will give this element (example for the group $(\mathbb{R^*}, \times)$, the neutral element is 1).
>- $\forall g\in G, \;\exists! g^{-1} : g\circ g^{-1} = g^{-1}\circ g = e$. That is, for any element of the group, one can find its unique inverse that by operating, will yield the neutral element.
>- $\forall g ,h \in G,\; g\circ h \in G \text{ and } h \circ g \in G$. In other words, the result of the operation between any 2 elements in $G$ will give an element that also belongs to $G$.

> Or more informally, we'll repeat ourselves - it's a set 
> either finite or infinite, that is closed (remember the notion
> of closure) under a operation, containing a identity element 
> and an inverse for every element.

This is quite an abstract concept, but also very common, when brought it with correspondance with real examples.


Apart from the exact notion of the group, there are multiple concepts related to it. For example, the notion of 
a __conjugacy class__ of a group. 

<u>Intuitively</u>, this can be though as a kind of a subset of this group containing elements, that share similar properties. 
More precisely, mathematically, one defines the conjugacy class $C$. 

> Two elements $x$ and $y$ belongs to the conjugacy class $C$:
> $$ y, x\in C \iff \exists u \in G :\; u^{-1}\circ x\circ u=y$$
In other words, elements $x,y$ of the group $G$, belong to the same conjugacy class if there is some kind of other element $u$ of $G$, such that they are related by $u^{-1}\circ x \circ u = y$.


It is not very easy to try to understand the meaning of this notion, since the general concept of groups is quite abstract.
We could interpret this as follows; let the group $(G, \circ)$ represent *some* kind of action. Then, two actions $x$ and $y$ belong to the 
same class if \
*performing the action $x$ results to the same action as performing some kind of action $u$, then $y$, then remove the action of the $u$ operation*.
In other words, the actions $x$ and $y$ are somewhat the 
same, in a different basis.

We could try to make an analogy with matrices/transformations.That 
is, we know there exists such a concept as change of basis. This concept gives the possibility, 
to express a matrix $A$ in two different basis. This is done via the change of base matrix $P$, namely, $A' = P^{-1}AP$. The matrix $A'$ represents
the exact 
same matrix as $A$, but in a different basis/from a different point of view.

## Symmetries 
We've mentioned that the notion of groups is an abstract concept and can be associated to many, even non purely mathematical conepts. 
For mathematics-related group examples, one can mention the
$(\mathcal{Z}, +)$ group (group of integers with the binary
operation of addition), the permutation group (the group 
consisted of permutation operations).
Here, we'll be interested in symmetries, and describe these 
symmetries using the notion of groups. 
Symmetries are geometrical transformations 
that can form a group. 

### Example
Let's provide an example of such transformation. Consider a triangle with equal sides with edges
denoted $A,B,C$. What are the transformations that could potentially make a group 
of symmetries? More simply put - what 
is the set of transformations that will leave the system invariant? 

- First, we have the identity element.
The identity operation does not change anything. 
- The second operation is the rotation by 120 degrees. This operation 
will map $A \mapsto B$, $B \mapsto C$ and $C\mapsto A$. However, the rotation by 120 degrees will not simply 
permute the edges of the triangle - it will also rotate the coordinates. Indeed, one can attach a fixed coordinate 
frame to every edge and make sure that these coordinates do indeed rotate with respect to the "fixed coordinate 
frame".
- The third operation is the rotation of the triangle by -120 degrees. This would be the exact same thing as 
the rotation by 240 degrees. 
- The fourth, fifth and the sixth operations are mirror operations. That is, if one reflects 
the triangle with respect to the bissectrice 
going from every single edge ($A, B$ or $C$).

By defining these 6 operations, one can 
create a group of transformations. It is 
indeed a group, since for all elements, there exist an inverse element and an identity element. 
This group is commonly reffered to as a $C_{3v}$ group.

For different shapes and symmetries and even dimensions (one can indeed consider a triangle in 2D or in 3D), one can come up with different groups.

In order to make the notation more consise, one can make arrange 
them in tables, often reffered to as the Cayleigh table.
The Cayleigh table keeps track of all possible operations in a group.
For an example, one can consider a simpler group $\mathcal{Z}_2$ 
commonly denoted as - the inversion group
or the permutation group of order 2, or $(\{0,1\},+)$ group.
This is nothing but the group of addition modulo-2. The operations here 
can be summarized as 
$$
0+0 \stackrel{\text{mod }2}{=} 0\\\\
0+1 \stackrel{\text{mod }2}{=} 1\\\\
1+0 \stackrel{\text{mod }2}{=} 1\\\\
1+1 \stackrel{\text{mod }2}{=} 0
$$
One may easily identify the neutral element $0$ and note that
this group is Abelian, meaning that all the elements commute.
And the corresponding Caleigh table for the group.
|+ |0 |1 |
|--|--|--|
| 0 |0 |1 |
| 1 |1 |0 |

There are 2 conjugacy classes in this group, namely, the neutral element
$\{0\}$ conjugacy class and $\{1\}$.
One can create the same Cayleigh table for the mentioned $C_{2v}$ 
group. These tables, are however, not very easy to manipulate for 
large groups. Indeed, for a group of $6$ elements, the table has 
$6\times 6 = 36$ entries in it. There are ways, however, to 
represent these groups in a more compact way. We will further see 
the notion of the _character table_, 
which can summarize its properties in a more 
compact manner.

Let's try to write down the Cayleigh table of the $\text{C}_{3v}$ group and analyze it using 
the properties we've defined above. 
So we've identified all the 6 transformatins belonging to this group. It can be shown 
that there exists only 2 typese of such groups. That means that one can 
come up with only two "different Cayleigh" tables for a group of order 6. 
Up to notation of course. 
In order to create the table, one can write down all the transformations we've encountered before. 
During the filling, one can ask ourselves at every intersection of the table:
> If I first do [transformation from top] and then do [transformation from right], 
> what would it be equivalent to?

For example, let's take one trivial case: first apply $e$ - the identity operation, and the apply 
$\sigma_A$ the mirror with respect to the bissectrice from the point $A$? It is clear the 
result will be $\sigma_A$, since the $e$ operation doesn't do anything...
What about a more complex case? First apply $C_1$-the rotation by $120$ degrees, and then the 
$\sigma_A$ mirror operation? This may not be very obvious, but it is quite easy to verify 
by drawing the 2 transformations. In fact, the 2 transformation 
will create some kind of permutation, and the final permutation has the 
mapping: $\sigma_A \circ C_2: A \mapsto C; B \mapsto B; C \mapsto A$. which 
is nothing but the $\sigma_B$ transformation. Thus, at the intersection 
of $C_1$ (top - first) and $\sigma_A$ (left - second), the resulting 
element will be $\sigma_B$.
By repeating this procedure $6\times 6$ times, one can obtain 
the Cayleigh table for the $C_{3v}$ group.

| | | | | | | |
|--|--|--|--|--|--|--|
|$\circ$    |$e$        |$C_1$      |$C_2$       |$\sigma_A$ |$\sigma_B$ |$\sigma_C$ |
|$e$        |  $e$      |$C_1$      |$C_2$       |$\sigma_A$ |$\sigma_B$ |$\sigma_C$ |
|$C_1$      |  $C_1$    |$C_2$      |$e$         |$\sigma_B$ |$\sigma_C$ |$\sigma_A$ |
|$C_2$      |  $C_2$    |$e$        |$C_1$       |$\sigma_C$ |$\sigma_A$ |$\sigma_B$ |
|$\sigma_A$ |$\sigma_A$ |$\sigma_C$ |$\sigma_B$  |$e$        |$C_2$      |$C_1$      |
|$\sigma_B$ |$\sigma_B$ |$\sigma_A$ |$\sigma_C$  |$C_1$      |$e$        |$C_2$      |
|$\sigma_C$ |$\sigma_C$ |$\sigma_B$ |$\sigma_A$  |$C_2$      |$C_1$      |$e$        |

So what can we say intuitively about this group? First, this group is not abelian, since 
performing 2 different operations in different order may not yield the same resulting state.
Second thing is that there are 3 (2) types of _"intuitive"_ transformations, namely, the 
identity transformation, the rotations (2 rotations) and reflexions (3 reflexions).
One may notice that on the table, there is some kind of pattern. Namely, the table can be 
divided into 4 quadrants - top left (TL), TR, bottom right (BR) and BL.
These quandrants can be characterized by the fact they only contain a specific type of transformations, i.e.
either the $\sigma$ 's or $C$ 's (without counting $e$). This can be intuitively interpreted as 
conjugacy classes, however, this is only a visual interpretation and is not always true and useful for larger groups.

In the $C_{3v}$ symmetry group, there are 3 conjugacy classes - the trivial one $\{e\}$, the rotations class 
$C \equiv \{C_1, C_2\}$ and the reflexions class $\sigma \equiv \{\sigma_A, \sigma_B, \sigma_C\}$.
What this means that if we take e.g. one element from the rotation class - some $C_i \in C$, then 
no matter which transformation of group $u \in C_{3v}$ we're taking; it can be the trivial identity ($u = e$), the element 
from the same conjugacy class ($u = C_k \in C$) or from the different conjugacy class ($u = \sigma_j \in \sigma$), 
we will always get that the result of $u^{-1}\circ C_i \circ u$ will be in the same conjugacy class as $C_i$, namely, in the 
conjugacy class $C \equiv \{C_1, C_2, ...\}$: $\; \; \;u^{-1}\circ C_i \circ u \in C$. \
Note: finding conjugacy classes is not always straightforward. 
They may obey the notion of "different types of transformations" 
as in the example with $C_{3v}$ (identity, rotations, reflexions),
but this is not always a matter of intuition. There 
exist databases and tables with groups and their corresponding 
partition into conjugacy classes.




## Representations 
Once again, as said, the notion of groups is very broad, and can 
be associated to many concepts. We've mentioned examples of 
groups, like $(\mathcal{Z}_2, +)$, particular matrix group 
like the $\text{SO}3$ group ( $3\times 3$ matrix of 
determinant $1$) and many others.

Here, the considered groups will be symmetries. That is, 
groups of geometrical transformations.


Representation theory is in a way a branch of 
group theory.
In representation theory, what we do is we associate groups to matrices.That is, symmetry operations
are associated to groups, which then are associated to matrices. 
> Thus, the idea of representation 
> theory to associate every element of a group to a matrix of any size.
> In addition to that, we want the association to be a homomorphism.  

$$
(G, \circ) \equiv \{e, g_1, g_2, ..., g_N\} \xrightarrow{\text{Mapping (homomorphism)}}
\{M_e, M_{g_1}, M_{g_2}, ...\}
$$

Before going into the notion of group __representation__, one would need a couple of notions.

> Let $f: G \rightarrow H$, a function that maps an element from the group $(G, \circ)$ to the group $(H,\star)$, i.e. $f: g \mapsto h$, with $g\in G$, $h\in H$.
> Then the function $f$ is a homomorphism if $\forall g_1, g_2 \in G$, $f(g_1\circ g_2) = f(g_1)\star f(g_2)$.
>
> A homomorphism $f'$, which is one-to-one (bijective) is an isomorphism.
Thus, intuitively speaking, a homomorphism is a map from a group to another 
group such that the operations inside the "target" group is the same as
in the "original" one. 

Now, one defines the central concept, i.e. the __representation of a group__. 
> Let $G$ some group. Let $V$ - some kind of vector space over some field of dimension $n$. 
> A representation of the group $G$ is a function $\Gamma$, sometimes denoted $\Gamma(G)$, defined by 
> $\Gamma(G): G \rightarrow \text{GL}(V)$, that is,
> $\Gamma(g): g \mapsto \text{gl}$, for some $g\in G$ and $\text{gl}\in \text{GL}(V)$. The representation $\Gamma$ 
> is a homomorphism.

Let's break down the definition. 
The $\text{GL}(V)$ is the __general linear group over the space V__, that is, it is a 
set of linear transformation in the space $V$ of dimension $n$. Similarly, $\text{GL}(V)$ in nothing but 
the space of $n\times n$ invertible matrices, that act on the vector space $V$. Note that this vector 
space can be arbitrary, e.g. $\mathbb{R}^n$, Hilbert space, or something else. 

In other words, the representation is a homomorphism (a function) that will map every element $g\in G$ to a matrix $M_g\in \text{GL}(V)$.
The space, to which $\Gamma$ maps the elements of $G$ is also a group (the group matrix). The values of these functions must obey the same rules as the 
elements $g \in G$. Thus, when saying "representation", one can refer to the most general $\Gamma$ as the set of mappings from $g\in G$ to elements in $\text{GL}(V)$.

That is, the term _representation_ itself encompasses the __mappings__ 
from elements $g\in G$ to elements in $\text{GL}(V)$, and NOT one 
particular matrix $M_g \in \text{GL}(V)$ associated to the element 
$g\in G$.

One can consider an example of a simple parity group of order 2. 
This group (sometimes denoted as $\mathbb{Z}_2$) has 2 elements: $\{e, p\}$ and they follow the 
same multiplication rules as $\{1, -1\} \equiv \{e, p\}$ 
or same additions rules as $\{0,1\}$ $\text{mod} 2$. 
One can try to create the representation $\Gamma$ for this 
group. Since the group is small, one can easily come up with a set 
of $2$ matrices, that will obey to the same multiplication 
rule as the group elements (see the Cayleigh table above).
These $2$ matrices are given by:

$$
\begin{pmatrix}
1 & 0 \\\\
0 & 1
\end{pmatrix} 
\equiv e, \quad 
\begin{pmatrix}
0 & 1 \\\\
1 & 0
\end{pmatrix} 
\equiv p
$$


which indeed follow the same multiplication rules as the group $\mathbb{Z}_2 \equiv \{e, p\}$. 
One must note that the group itself, containing $\{e,p\}$ is an abstract group, which simply has multiplication rules $e\cdot p = p\cdot e= p$; $p\cdot p = e$ and $e \cdot e = e$. 
The group has nothing to do with matrices or even $\mathbb{Z}_2$. Indeed, the group is anything that will obey these kind of relations. The representations, however, 
do indeed have a relation with matrices and $\mathbb{Z}_2$. In other words, one can come up with 2 representations:

$$
\Gamma _{\mathbb{Z} _z}: e \mapsto 1,  p\mapsto -1 
$$

$$
\Gamma _{\text{GL}(V)}: e \mapsto 
\begin{pmatrix}
1 & 0 \\\\
0 & 1
\end{pmatrix} 
, p \mapsto 
\begin{pmatrix}
0 & 1\\\\
1 & 0
\end{pmatrix} 
$$
both representations are valid. Indeed, the two elements of $\mathbb{Z}_2$ are indeed elements of $\text{GL}(V)$ of dimension 1 and the two matrices are elements 
of $\text{GL}(V)$ of dimension 2.

In quantum mechanics, as said, we're working with finite groups, that are groups of symmetry. 
The group represents the symmetry of inversion.

Now, one should introduce the concept of __reductibility__. 
Consider a symmetry group $G$ that describes some system. And let $\Gamma$ be its representation. 
Let now $\Gamma (g)$ be a representaion, that acts on the vector space $V$. One says that this 
representation is completely reducible if there exists a non-zero subspace $W \in V$, that is invariant 
under $\Gamma$. In other, words, it is reducible if there exists a subspace $W \in V$, such that 
$\forall \ket{w} \in W$, such that $\Gamma (g) \ket{w} \in W$, which is true __FOR ALL__ $g\in G$. In addition 
to that, the subspace $W^\text{T}$ is orthogonal to $W$. One can visualize 
it in terms of matrices. That is, $\Gamma (g)$ is reducible if for all $g\in G$, one can put the matrices $\Gamma$ 
in the form 
$$
\Gamma (g) \equiv
\begin{pmatrix}
\Gamma(g) ^{(1)} & 0 \\\\
0 & \Gamma(g) ^{(2)} \\\\
\end{pmatrix}
= \Gamma(g) ^{(1)} \oplus \Gamma(g) ^{(2)}
$$
Where the two matrices $\Gamma (g) ^{(1),(2)}$ are also matrices and the matrix $\Gamma (g)$ is diagonal by blocks. A reducible 
representation is a representation that can be block-diagonalized more and more. A representation that is already "maximally 
reduced", is called irreducible representation.

Since the representation we're considering are matrices, there should be a way to go from a reducible to irreducible representation. 
This could be done via a change of basis matrix. Namely, one can write 
$$
\Gamma(g) _{\text{red}} = S^{-1} \Gamma(g) _{\text{irred}} S
$$

This relation is called an equivalence relation. That is 2 representations are equivalent if there exists a basis that transforms them as 
given above. This relation is called a similarity transformation. In other words, 2 equivalent representations are related via 
a similarity transformation. 

In representation theory, we're interested in __non-equivalent__, but __irreducible representations__. That is, in representation theory, 
two representations, are "the same" if they are irreducible and 
possibly equivalent.
One should, however, note another fact concerning the reducible representations. The general matrix form of the irreducible 
representation is instead given by 
$$
\begin{pmatrix}
\Gamma(g) _1 ^{(1)}      & 0 &0 &0 & 0          & 0\\\\
0 & \Gamma(g) _2 ^{(1)}  &0    &0 &0       & 0\\\\
0 & 0 & \ddots           & 0     &0          &0   \\\\
0 & 0 & 0                  & \Gamma(g) _1 ^{(2)} &0 &0            \\\\
0 & 0 & 0                  &  0& \Gamma(g) _2 ^{(2)} & 0          \\\\
0 & 0 & 0 & 0 & 0 & \ddots
\end{pmatrix}
$$

That is, the representation, in its most general case, is decomposed as 

$$
\Gamma(g) = \bigoplus_{a,x} \Gamma(g)^{(a)}_{x}
$$

instead of simply $\Gamma(g) = \bigoplus _{a} \Gamma(g)^{(a)}$. That is, one adds some degenerescence to a given 
element of the block-representation $\Gamma(g)^{(a)}$. 

This is a very important formula that describes 
well the notion of (ir)-reducible representations.

### Why do we need it? Recap up to now
- So for now what we understand is that there exists some kind of spatial structure 
(a triangle, cube, molecule, etc...) that has some symmetry associated to it. What 
symmetry means is that one can apply one of the symmetrical transformation, and we won't 
be able to tell the difference between the systems before and after transformations.

- These symmetries obey to some mathematical properties between themselves. These 
mathematical properties are called a group.

- Instead of working with the group, which can be characterized using a Cayleigh table 
(containing all possible relations in the group), one can characterize the group 
using the representation theory. This is equivalent, since a representation is 
an isomorphism by definition. That means that the relations of all the elements 
with all the elements is the same as the relations between the matrices that form 
this representation (recall that a representation is mainly a association between 
abstract elements of a group to "real"/"tangible" matrices).

- The set of matrices (the representation) can be different. Indeed, the matrices
is a representation as long as it obeys the necessary relation from the group.

But what could we eventually need this for? Suppose the (symmetric) system that we
are analyzing is somewhat a physical object (most likely a molecule). We want 
to retrieve and compute some of its properties. This will be most likely done 
through a Hamiltonian operator, which can be represented as a matrix.
The Hamiltonian will also most likely lead to the solution of an eigenvalue problem, thus 
requiring diagonalization. 
The next question is thus "what does the Hamiltonian have to do 
with the symmetry transformation matrix (representation)?"
Well, the answer to this makes sense - __they commute__. 
Indeed, the symmetry transformation is by definition a transformation 
that takes into account symmetry and the system is unvariant under this 
transformation, meaning the Hamiltonian does not change either.
From linear algebra, this commutative property leads to another mathematical property:
if 2 operators are commuting, it is possible to find a __common__ basis, such that 
both of the commuting operators will by (block) diagonal.
So, if the symmetry matrix is _nice_ and _easy_, one can 
diagonalize the latter and work our way to the diagonalization of the hamiltonian itself.

- Now, what does the notion of reducible/irreducible has to do with that? When 
discussing the representations, we mentioned that we're especially interested 
in __irreducible__ representations, which, by definition are 
block-diagonal. This means that irreducible representations are matrices
of symmetry transformations (i.e. obeying the group rules), but meant to 
be easy manipulated.

- Thus the goal of the representation theory 
is: 
> based on symmetry considerations, find a valid representation, and then reduce it 
> in order to obtain the simplest form possible
> using maths from representation theory. Once this is done, 
> it is possible to infer some properties of the system, and potentially 
> solve the eigenvalue problem for the complex hamiltonian, 
> since the irreducible representation have 
> a simpler structure.



## Mathematical description
Before going into the practical examples, trying to understand 
the role of the notion of group representations and how could that be 
useful, one should simply mention, without proving, some 
of important theorems & concepts. These concepts are tools, that 
are used to accomplish the goal that we've written above.

### Shur Lemma's 
The Shur's Lemma's is the central theorem in the group 
representation theory. Namely, many results can be 
~~simply~~ derived from the definitions and the mentioned Shur's 
lemmas.
For Shur's Lemmas, let $\Gamma_1$ and $\Gamma_2$ - two different 
__irreducible__ representations each belonging 
to its own vector space $V_1$ and $V_2$ respectively  
(for example, the two representations could be matrices of size 
$3\times 3$ and $2\times 2$ acting 
on $\mathbb{C}^3$ and $\mathbb{C}^2$). Let in addition $M$ be a operator (matrix) $M: V_1 \mapsto V_2$,
such that it commutes with both of the representations 
$\Gamma_{1,2}$. That is, $M\;\Gamma_1(g) = \Gamma_2(g)\; M
\;\; \forall g \in G$, then

| Shur's Lemma 1| Shur's Lemma 2|
|--|--|
|If $\Gamma_1$ and $\Gamma_2$ are not-equivalent, then $M=0$|If $\Gamma_1 = \Gamma_2 \equiv \Gamma$, then $M$ can only be the multiple of identity, that is, $M$ has the form $M\equiv \lambda I$|

These two lemmas state that if some operator commutes
with some two representations of a group, then 
this operator is either zero (the two representations 
are equivalent) or diagonal (if they are the same).
> Note: We mentioned in one of the previous sections
> how representations are useful. Here, the matrix 
> $M$ in question can be nothing but our Hamiltonian.

### Characters
By now, we came across some mathematical objects such as 
group, subgroup, isomorphism, representation. It is now 
time to add a new one - the character. 
We've mentioned that in representation theory, 
we're interested in representations, up to an equivalence 
relations (i.e. equivalent representations 
are considered to be the same). Thus, we may want 
to somehow characterize a representation (remember the 
definition of the representation - set of matrices), without 
having to deal the problem of cheking 
the equivalence. \
The answer to that is the trace of the matrix. The set 
of traces of a representation is its __character__.
One denotes a character of a matrix $\chi_\Gamma(g)$ of 
the representation $\Gamma$ of the matrix $\Gamma(g)$. 
That is, $\chi_\Gamma(g)=\text{Tr}[\Gamma(g)]$.
One should recall the properties of the trace - 
$\text{Tr}(A\oplus B) = \text{Tr}(A)+\text{Tr}(B)$ and 
$\text{Tr}(A\otimes B) = \text{Tr}(A)\cdot \text{Tr}(B)$.

### Orthogonality
We mentioned that should be able to decompose a representation 
into a direct sum of irreducible representations.
That is, we want to decompose the representation (which 
possibly can be reduced) into the direct sum of irreducible: 
$\Gamma = \bigoplus_{a,x}\Gamma_{a,x}$, with $a$ - the 
irreducible representations and $x$ - the corresponding 
multiplicities or $\Gamma = \bigoplus_{a} b_a \Gamma_{a}$ and 
$b_a$ - the multiplicities. The resulting representation consists of 
a direct sum of vector spaces $\bigoplus_{a,x} V_{a,x}$.
For every space $V_{a,x}$, one my identify a basis $\{\ket{j}\}$.
One can denote the basis $\{\ket{j}\}$ belonging to 
the space $V_{a,x}$ as $\{\ket{a,j,x}\}$. 
Thus the basis of a given representation is denoted 
as $\{\ket{a,j,x}\}$. 

The orthogonality theorem is an important result, that 
can be shown using the Shur's lemmas (not done here)\
Let $\Gamma_a$ and $\Gamma_b$ - two non-equivalent 
representations 
over the space $V_a$, $V_b$ of dimensions $n_a$ and $n_b$, of
the group $G$ of order $N$. Then, the great orthogonality 
theorem states: 
$$
\sum_{g\in G}\frac{n_a}{N} [\Gamma_a(g)]^*_{i,k}[\Gamma_b(g)]_{m,n} =\delta_{a,b}\delta_{i,m}\delta_{k,n}
$$
Where the sum is performed over the group elements $g\in G$
and $[\Gamma_b(g)]_{m,n}$ the element at $(m,n)$ of the 
matrix $\Gamma_{a}$ . 
This can be easily rewritten as 

$$
\sum_{g\in G}\sqrt{\frac{n_a}{N}} [\Gamma_a(g)]^*_{i,k} \sqrt{\frac{n_b}{N}}[\Gamma_b(g)]_{m,n} =\delta_{a,b}\delta_{i,m}\delta_{k,n}
$$
and identifying the mentioned elements of the vector space 
$\ket{a,k,j} \equiv \sqrt{\frac{n_a}{N}} [\Gamma_a(g)]^*_{j,k} $.
The basis ortogonality relation can be identified as 
$\braket{b,i,k|a,m,n}=\delta_{a,b}\delta_{i,m}\delta_{k,n}$.

Based on the orthogonality relations, it is possible 
to derive the Burnside lemma, which gives a restriction to 
dimensions of the irreducible vector spaces $n_a$:
$$
\sum_{a}n_a^2 = N
$$
That being said, the sum of squares of the dimensions of the 
vector spaces into which the representations are operating is 
equal to the order of the group.\
The Burnside Lemma is quite useful for determining the dimensions of 
representations of groups of small order. That is, suppose 
there exists a group of order $6$. Then, based on Burnside's lemma, 
one state that a possible irreducible representation 
will be made of $6$ representations of dimension $1$. Indeed, 
$\sum_{a\in |\Gamma_a|}n_a^2=6\cdot 1^2 = 6 = N$, where $|\cdot|$ 
stands for cardinality/size and $N$ the size of the group. 
Or, another possibility is to have 
$1$ representation of dimension $2$ and $2$ representations of dimension 
$1$. Indeed, $\sum_{a\in |\Gamma_a|}n_a^2=1^2+1^2+2^2=6=N$.
Similarly, for e.g. a group of size $8$, based on only Burnside, 
there can be either $8$ irreducible representations 
of dimension 1 ($8\cdot 1^2 = N$), or $1$ representation of dim. 
$2$ and $4$ of dim. $1$ ($2^2 + 1^2+ 1^2+ 1^2+ 1^2 = N$) or simply 
$2$ representations of dimension $2$.\
If in addition, we know, how many conjugacy classes there is, it is 
even easier to determine the dimensions of the representations.
That is, suppose some kind of group of order $10$ contains 
$4$ conjugacy classes. Then, there are $4$ irreducible representations.
It is straightforward to find out the dimensions of the $4$ irreducible 
representations - they are $2^2+2^2+1^2+1^2 = N = 10$.

If one takes the trace of the mentioned orthogonality relation, 
one gets the second orthogonality theorem relation:
$$
\sum_{g\in G} \chi_a(g) \chi_b(g) = N\delta_{a,b}
$$
or equivalently, one can replace the group elements $g\in G$
by the elements of the conjugacy class, since we remember that the
characters are same for all the elements in the conjugacy class.
Thus, the equivalent relation is given by

$$
\sum_{\mu \in N_{\text{conj. cl.}}} n_{\mu} \chi_{a}^*(C_\mu)\chi_{b}(C_\mu)=N\delta_{a,b}
$$
with $n_\mu$ - the number of elements in the conjugacy 
class.

The degeneracies $b_a$ mentioned before can be computed using 
the relation

$$
b_a = \frac{1}{N}\sum_{\mu} n_\mu \chi_{a}^*(C_\mu)\chi_{\Gamma}(C_\mu)
$$
with $\chi_{\Gamma}(C_\mu)$ the character of the $C_\mu$ 
conjugacy class.

One may add the last relation that gives necessary and 
sufficient conditions for a representation to be irreducible. 
$$
\sum_{\mu} n_\mu |\chi_\Gamma(C_\mu)|^2 = N
$$

### Projectors
Projectors are operators that let us decompose and reduce a representation. 
Recall the goal of problem related to representation theory - to reduce a representation 
of some symmetric system. Mathematically, given a representation of a symmetry 
group $\Gamma$, one wants obtain the direct sum decomposition:
$$
\Gamma = \bigoplus_{a,x} \Gamma_{a,x} = \bigoplus_{a} b_a \Gamma_a
$$

The space that the resulting representation will be _acting_ on will be the exact same 
direct sum of $V_a$ spaces, each being orthogonal. This is equivalent 
of finding a representation in the basis that we called $\{\ket{a,j,x}\}$.
Let's now see how we'll try to define the projectors. 
We start by considering a vector $\ket{a,j,x}$ and the representation $\Gamma$.
What happens, when we apply the representation to this element 
$\Gamma (g) \ket{a,j,x} $?
Well, we remember that the $a$ in the ket notation represents 
the number of the non-equivalent irreducible representation, 
that the initial representation was reduced to. The $x$ represents its 
multiplicity and only the $j$ represents the _"actual" vector_ inside this $V_{a,x}$ 
vector space.
The usual matrix multiplication definition:
$$
\Gamma \ket{a,j,x} = \sum_{k=1} (\Gamma)_{k,j} \ket{a,k,x}
$$

But we know that for a given $a$ and $x$, the spaces are orthogonal, so the only
non-zero contribution comes from the $\Gamma_{a,x}$ representation:

$$
\Gamma \ket{a,j,x} = \sum_{k=1} (\Gamma)_{k,j} \ket{a,k,x}
$$

Using this and the previous orthogonality relations, one can transform it by doing some algebra into:
$$
\sum_{g \in G} [ \Gamma_b (g)]^{*}_{k',j'} \; \Gamma (g) \ket{a,j,x} = \frac{N}{n_a} \delta _{a,b} \delta _{j,j'} \ket{a,k',x}
$$

from which, one defines the projection operator $\hat{\Pi}_{k,j}^{b}$, which is defined as

$$
\hat{\Pi} ^{b} _{k,j} = \frac{n_a}{N} \sum _{g \in G} [\Gamma _b (g)]^{*} _{k,j} \Gamma _{g}
$$

which will satisfy the following 
properties:

$$
\hat{\Pi} ^{a} _{k,j} \ket{a,j,x} = \ket{a,k,x} 
$$

$$
\hat{\Pi} ^{a} _{k,j} \ket{a,j',x}  = 0
$$

This projector $\hat{\Pi}_{k,j}^{a}$ projects an arbitrary vector onto the vector $\ket{a,k,x}$.
If applied on another, orthogonal vector of $\ket{a,j,x}$, the result will be zero.


### Idea of how use the representations?
Now, with all that in mind, one can complete the discussion on how are representations useful 
and used.\
Let's suppose we're given some kind of symmetric system that represents, for example, some 
kind of molecular structure or multiple moleculesm, that is unvariant under some kind of transformations.
The first thing is to identify the abstract symmetry group.
Once identified, one should find (or construct the character table (see below)). 
The character table gives almost all the information needed for reducing the 
representation. 
For example, what if one wants determine the degeneracies of the eigenvalue problem? That is, 
how many times is a certain energy degenerate. Remember, the number of degeneracy of an operator 
is equal to the dimension of the eigenspace. Now, we remember that the 
representation of the system WILL commute with the Hamiltonian. Thus, by 
identifying the multiplicities $b_a$'s (see identity above), one can find out the 
degeneracy of the subspace, associated to the same representation.

One often may want to solve the motion of the system (e.g. $x(t)$, $p(t)$ or any 
general function $\psi(x,t)$). Then, once again, using the fact that the 
commutator of the Hamiltonian and $\Gamma$ is zero, one finds the seeked 
solution of the general eigenvalue problem, encountered in quantum mechanics 
$\hat{H}\ket{\psi} = E\ket{\psi}$. To solve this, one can consider the matrix $\Gamma$ 
instead and compute the eigenvectors and eigenspaces. 
The latter is often performed using the projectors.

## Worked examples
We're finally in a position of starting considering concrete examples and 
apply the mentioned concept for solving quantum mechanical problems.
This is the most important part of the article, where we will try to understand 
the mentioned notions by applying them, since the considered concepts tend to be quite 
abstract.

### Simplest group - reflection group
We start off by considering the simplest, already mentioned group - the reflection group/ parity 
group/ $C_s$ group. This group has lots of names, since, as we've seen a group 
can be associated to many different notions. The main point 
is that the $C_s$ group has $2$ elements and there is only 
one possible group of order $2$.
It's Cayleigh table is given by 

$$
\def\arraystretch{1.5} \begin{array}{|c|c|c|}
\hline
   \circ & e & p \\\\ 
   \hline
   e & e & p \\\\
   \hline
   p & p & e \\\\
   \hline
\end{array}
$$
This is a very simple group and it is quite easy to determine the irreducible 
representations. Indeed, let's recall the 
burnside lemma. From the Burnside lemma, one can determine that there are 
$2$ irreducible representation of dimension $1$, i.e. $\Gamma = \Gamma_1 \oplus \Gamma_2$, 
with both $\Gamma_1$ and $\Gamma_2$ of dimension $1$.
Thus the representation are simply $2$ numbers. It is quite easy to find that the 2 
representations the following:

$$
\def\arraystretch{1.5} \begin{array}{|c|c|c|}
\hline
    & e & p \\\\ 
   \hline
   \Gamma_1 & 1 & 1 \\\\
   \hline
   \Gamma_2 & 1 & -1 \\\\
   \hline
\end{array}
$$
We can check that this is true - if $e \mapsto 1$, and $p \mapsto 1$, the relations 
within the group are verified. Similarly, if $e \mapsto 1$ and $p \mapsto -1$, the relation is still verified.
Now, what about the most powerful tool available - the character table? What does it look like? Well, 
in order to find out, one must simply take the trace of the representaions. Here, the representations 
are simply numbers, thus the trace is equal to the number itself. So the character table:

$$
\def\arraystretch{1.5} \begin{array}{|c|c|c||c|}
\hline
    \chi & e & p & \text{Linear funcs. and rotations } \\\\ 
   \hline
   \Gamma_1 & 1 & 1& x,y, R_z \\\\
   \hline
   \Gamma_2 & 1 & -1& z, R_x, R_y\\\\
   \hline
\end{array}
$$
Well, this was quite easy... However, let's suppose we don't know the irreducible decomposition, and 
we try to start from the physical situation.
We have a simple molecule having $2$ atoms - left and right ones denoted as $L$ and $R$.
Their coordinates are given by $L \equiv (0, 0, z=-z_0)$ and $R \equiv (0, 0, z=z_0)$. 
This can be a 3-dimensional system, but we can always choose a coordinate system so that 
only one of the components is non-zero; in this case, we take $z$.

Now, we ask ourselves an important question - what will happen when the reflection 
transformation is applied? We have that the left one becomes the right one and the 
right one becomes the left one. Thus, the 2 transformations in the matrix form (the ID 
transformation and the permutation transformation) are given by 
$$
e \equiv
\begin{pmatrix}
1 & 0 \\\\
0 & 1 \\\\
\end{pmatrix} 
\\;\\;\\;\\;\\;\\;\\;\\;
p \equiv
\begin{pmatrix}
0 & 1 \\\\
1 & 0 \\\\
\end{pmatrix} 
$$

Now, one considers the character table that we've provided above and observe that there are 2 
conjugacy classes: $\lbrace e \rbrace$ and $\lbrace p \rbrace$.
Therefore, one can apply the different concepts we've mentioned before to determine the 
different vibrations of the molecule.\
We know that there are 2 conjugacy classes thus we know that we will have $2$ representations
of dimensions $1$. We can verify it mathematically, using the formula for $b_1$ and $b_2$. 
Let's start with the formula:

$$
b_a = \frac{1}{N}\sum_{\mu} n_\mu \chi_{a}^*(C_\mu)\chi_{\Gamma}(C_\mu)
$$

then, using $N=2$ and $a \equiv 1$
$$
b_1 = \frac{1}{2}\sum_{\mu} n_\mu \chi_{1}^*(C_\mu)\chi_{\Gamma}(C_\mu) = 
\frac{1}{2} ( 1\cdot 2 \cdot 1 + 1\cdot 0 \cdot 1 ) = \frac{2}{2} = 1
$$
where we have used that $\chi_{1} = 2$ (trace of matrix associated to $e$) and $\chi_2 = 0$, and 
the character of $\Gamma$ $\chi_{\Gamma}(C_\mu)$ is taken from our character table.
Similarly, 

$$
b_2 = \frac{1}{2}\sum_{\mu} n_\mu \chi_{2}^*(C_\mu)\chi_{\Gamma}(C_\mu) = 
\frac{1}{2}(1 \cdot 2 \cdot 1 + 1\cdot 0 \cdot (-1)) = 1
$$
which shows our initial Burnside lemma of $2$ representation of dimensions $1$.

Remember we mentioned that we can come up with 
different representations. Here, we can add another one - 
namely, we can consider the problem in terms of coordinates 
transformations, rather than in terms of element permutation. 
The transformation will keep $(x,y)$ unchanged and the will flip 
the $z$ coordinate. The resulting transformation 
matrix is therefore given by 
$$
\begin{pmatrix}
1 & 0 & 0\\\\
0 & 1 & 0 \\\\
0 & 0 & 1 \\\\
\end{pmatrix} 
\equiv e, \quad 
\begin{pmatrix}
1 & 0 & 0\\\\
0 & 1 & 0 \\\\
0 & 0 & -1 \\\\
\end{pmatrix} 
\equiv p
$$




> This multiplicity notion can be interpreted as follows. The representation acts on the vector space $V$. The operations 
> that are 
> represented on $V$ are related to the group symmetries. That is, in the group, there are elements that get transformed in the same 
> manner. That is, suppose we consider the group $D_4$, which is the group of symmetric transformations of a square (e.g. of points 
> located at the edges of a squares), which vertices are numbered from the top LHS in the clockwise direction (see the figure). 
> Then, one considers the element of the group that transforms the square by flipping it along the diagonal in red. Then, clearly, the 
> position 1 \& 3 are not changed. This means that the elements $1$ and $3$ are transformed in the same manner. That is, they are 
> _not_ transformed (or transformed as identity).
>
> In this example, we've considered the group $G \equiv D_4$, and the space, to which it gets mapped via the representation $\Gamma$ is 
> the position space. That is, we map one transformation of the group to the space of positions (e.g. a rotation in the group space corresponds to the cartesian coordinates, described by e.g. the cartesian $(x,y,z)$ ). Thus, the diagonal transformation does not change the position 
> of the points $1$ and $4$.
> 
> This invariance corresponds to the degeneracy of the group representation that we've mentioned in the decomposition of the 
> irreducible representation.

|![](/images/d4_symm.drawio.png)|
|:--:|

## Examples
We've seen that representations is a way to link the abstract notion of groups to a more common 
notion of matrices. Now, one will try to link the notion we've discussed. That is, lets consider 
the simplest parity group.
### Parity group
Consider a molecule made of 2 atoms tighten with 1 bond. One denotes the atom on the left as atom $A$ and the atom on the 
right as atom $B$. Using the concept of particle indisinguishability, if we exchange $A$ and $B$, we won't be able 
to tell the difference. Therefore, one can say that there is a symmetry of the given system. Indeed, we can make the transformation 
$A \mapsto B$ and $B \mapsto A$. Then, as mentioned, one can come with the representation 

[privesti primer sejchas, i jeshe pozhe o tom, chtom mozhno sdelatj neskoljko representations. Naprimer 
[0,1; 1,0] dlja nechetnoj funkcii, ili naprimer [-1, 0; 0, 1]. Rassmotretj eti dve representations.]
