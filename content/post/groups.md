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
Let's provide an example of such transformation. Consider a triangle with equal sides with edges
denoted $A,B,C$. What are the transformations that could potentially make a group? First, we have the identity element.
The identity operation does not change anything. The second operation is the rotation by 120 degrees. This operation 
will map $A \mapsto B$, $B \mapsto C$ and $C\mapsto A$. 
By defining these 5 operations, one can 
create a group of transformations. It is 
indeed a group, since for all elements, there exist an inverse element and an identity element. 
This group is commonly reffered to as a $C_{2v}$ group.

For different shapes and symmetries, one can come up with different groups.
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

Before going into the practical examples and trying to understand 
the role of the notion of group representations and how could that be 
useful, one should simply mention, without proving, some 
of important theorems & concepts

### Shur Lemma's 
The Shur's Lemma's is the central theorem in the group 
representation theory. Namely, many results can be 
~~simply~~ derived from the definitions and the mentioned Shur's 
lemmas.

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


 

















