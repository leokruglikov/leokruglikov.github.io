---
title: "Quantum operator cheat sheet"
date: "2023-05-17T22:33:44+01:00"
draft: true
tags: ["physics"]
katex: true
markup: "mmark" 
showReadingTime: true
toc: true
---
## Quantum mechanics postulates 
Quantum mechanics is sometimes not intuitive. For that, states postulates that serve as axioms for quantum mechanics.
### Hilbert space 
A quantum state, describing a system is denoted with a ket and lives in it's state space, which is a Hilbert space.
The latter can be either finite or infinite. One denotes

$$
\ket{\psi} \in \mathcal{H} 
$$
The state can be sometimes represented as a member of $\mathbb{C}^d$, i.e. a column vector.

### Measurements
In quantum mechanics, a measurement is represented by an operator. 
The measurement operator is must be Hermitian. Consider an operator
$\hat{A}$. Since it is hermitian, we can decompose it in eigenkets $\ket{a_i}$ and eigenvalues $a_i$.
That is, 
$$
\widehat{A} = \sum_i a_i\ket{a_i}\bra{a_i}
$$
Note that this is the case for a discrete operator. The case of a continious spectrum will be mentioned further.\
In addition to that, one can decompose any state $\ket{\psi}$ into the eigenkets. 
That is, 
$$
\ket{\psi} = \sum_i c_i \ket{a_i}
$$
The main postulate of the quantum measurement states that after the measurement, the state collapses 
to one of the eigenvalue of the $\ket{a_i}$. This, in addition happens with probability $|\langle \psi | a_i \rangle|^2$. \
**Note**: The measurement postulate will be elaborated more.

## Measurements
The quantum measurement operators are given by a set $\hat{M}_i$, which obey $\sum_i \hat{M}^{\dag}_i \hat{M}_i = \mathbb{I}$
Suppose we're measuring $\hat{M}_i$ on $\ket{\psi}$. Then, the state $\ket{\psi}$ will collapse into a new state.
The collapse/transformation is given by 
$$
\ket{\psi} \mapsto \frac{\hat{M}_k\ket{\psi}}{\sqrt{p_k}} \equiv \ket{\psi_k}
$$
Where $p_k$ is the probability that the state $\ket{\psi}$ collapses to the state related to the $\hat{M}_k$.
This is given by 
$p_k = \langle \psi | \hat{M}_k^{\dag} \hat{M}_k | \psi \rangle$

## General properties of commutators
Let $\hat{A}$, $\hat{B}$ and $\hat{C}$ - operators. Then, 

- $[\widehat{A}, \widehat{B}]=-[\widehat{B}, \widehat{A}]$
- $[\widehat{A}, \widehat{A}]$
- $[\widehat{A}+\widehat{B}, \widehat{C}] = [\widehat{A}, \widehat{C}] + [\widehat{B}, \widehat{C}]$ 
- $[\widehat{A}, \widehat{B}+\widehat{C}] = [\widehat{A}, \widehat{C}] + [\widehat{A}, \widehat{B}]$
- $[\widehat{A}, \widehat{B}\widehat{C}] = [\widehat{A}, \widehat{B}]\widehat{C}+\widehat{B}[\widehat{A}, \widehat{C}]$
- $[\widehat{A}\widehat{B}, \widehat{C}] = [\widehat{A}, \widehat{C}]\widehat{B} + \widehat{A}[\widehat{B}, \widehat{C}]$
- Suppose that the 2 operators $\widehat{A}$ and $\widehat{B}$ commute with their commutator. That is, $[\widehat{A},[\widehat{A},\widehat{B}]]=0$ 
and $[\widehat{B},[\widehat{A},\widehat{B}]]=0$, then 
  - $[\widehat{A}, \widehat{B}^n] = n\widehat{B}^{n-1}[\widehat{A}, \widehat{B}]$
  - $[\widehat{A}^{n}, \widehat{B}] = n\widehat{A}^{n-1}[\widehat{A}, \widehat{B}]]$

## Position and momentum
Here one considers two operators, namely, the position operator, $\widehat{\vec{x}}$, with $\widehat{\vec{x}} = \widehat{x}_1 + \widehat{x}_2 + \widehat{x}_3$, 
where $\{1,2,3\}$ corresponds to $\{x,y,z\}$. The second operator is the momentum operator, similarly defined as $\widehat{\vec{p}}$, 
with $\widehat{\vec{p}} \coloneqq \widehat{p}_1 + \widehat{p}_2 + \widehat{p}_3$. 

Their famous commutation relation reads:

$$ [ \widehat{\vec{x}_i}, \widehat{\vec{p}_j} ] = i \hbar \delta _{i,j} \mathbb{1}
, \quad \text{with } \widehat{\vec{p}}\equiv \frac{\hbar}{i}\vec{\nabla} = -i\hbar \vec{\nabla} $$ 
One also notes that the components of the $\widehat{\vec{x}}$ and $\widehat{\vec{p}}$ commute between each other.

The operators commute with their respective commutator. That is, 
$$ [\widehat{\vec{x}}_k,[\widehat{\vec{x}}_i, \widehat{\vec{p}}_j]] =
\widehat{\vec{x}}_k[\widehat{\vec{x}}_i, \widehat{\vec{p}}_j] - [\widehat{\vec{x}}_i, \widehat{\vec{p}}_j]\widehat{\vec{x}}_k = \\ $$
$$ 
= \widehat{\vec{x}}_ki\hbar\delta _{i,j} - i\hbar\delta _{i,j}\widehat{\vec{x}}_k = 0 $$
 $$ \qquad \qquad, \text{since the operator } \delta _{i,j} \text{ commutes with the rest} $$

## Harmonic oscillator
The harmonic oscillator is a classical yet important problem in quantum mechanics. 
The hamiltonian for the harmonic oscillator is given by 
$$
\mathcal{H} = \frac{\hat{p}^2}{2m} + \frac{1}{2}m\omega^2\hat{x}^2
$$
One defines the creation and anihilation operators respectively
$$
\hat{a} = \frac{1}{\sqrt{2}}\Biggl(\sqrt{\frac{m\omega}{\hbar}}\hat{x} + i\frac{1}{\sqrt{m\omega \hbar}} \Biggr) \\\\
\hat{a}^{\dag} = \frac{1}{\sqrt{2}}\Biggl(\sqrt{\frac{m\omega}{\hbar}}\hat{x} - i\frac{1}{\sqrt{m\omega \hbar}} \Biggr) 
$$
They obey the commutation relation 
$$
[\hat{a}, \hat{a}^{\dag}] = 1
$$
And the hamiltonian $\mathcal{H}$ can be written using those operators:
$$
\mathcal{H} = \hbar \omega \biggl( \hat{a}^{\dag} \hat{a} + \frac{1}{2} \biggr)
$$


## Momentum operator
The angular operator may refer to different notions, since it is quite a general formulation. Namely, this may refer to 
the *orbital* angular momentum operator $\widehat{\vec{L}}$, to the *spin* angular momentum operator $\widehat{\vec{S}}$ or 
to the *total* angular momentum operator $\widehat{\vec{J}} = \widehat{\vec{L}} + \widehat{\vec{S}}$.
The names are similar, since they have many common characteristics. Namely, e.g. the commutation relations. 
The most general angular momentum $\hat{\vec{\jmath}}$ is characterized by the commutation relation 

$$ \hat{\jmath}_i, \hat{\jmath}_k  = i\hbar \epsilon _{klm}\hat{\jmath}_k, \text{ where } k,l,m \in \{x,y,z\} , \text{ the components of } \hat{\vec{\jmath}}
$$
with the definition $\widehat{\vec{\jmath}}^2 = \widehat{\jmath}^2_x + \widehat{\jmath}^2_y + \widehat{\jmath}^2_z$. One 
can choose a basis, in which the measurements are performed. The chosen basis is taken commonly $\hat{\jmath}_z$. 

Based on the 2 operators $\widehat{\vec{\jmath}}^2$ and $\widehat{\jmath}_z$, one defines the state $\ket{m \jmath}$, 
describing the angular momentums. The operators on this state give

$$ \hat{\vec{\jmath}}^2 \ket{\jmath m} = \jmath(\jmath + 1) \ket{\jmath m} \qquad \qquad 
\hat{\jmath}_z \ket{\jmath m}
 = m\ket{\jmath m} \\\\
\qquad \qquad \qquad \qquad \qquad \qquad \text{ with }\jmath \text{ a scalar eigenvalue related to } \\\\ 
\hat{\vec{\jmath}}^2 \text{  and } m \text{ related to } \hat{\jmath}_z 
$$

Since $\widehat{\vec{\jmath}}^2$ is an operator that, in a way, describes the module of the other components 
$\widehat{\jmath}_{x,y,z}$, there is a relation between the eigenvalues $\jmath$ and $m$. Namely, the famous relation reads

$$
\jmath \equiv 0, \frac{1}{2},1, \frac{3}{2} ... 
\quad \text{ or } \jmath
\equiv 0, 1, 2, 3, ... \quad \text{ and } \quad m \equiv [ -\jmath , -\jmath +1 , ..., \jmath -1, \jmath ]
$$

In addition, one can define for convenience other operators - __creation__ and __anihilation__ operators. One defines 
$$
\widehat{\jmath}_+  = \widehat{\jmath}_x + i\widehat{\jmath}_y \\\\
\widehat{\jmath} _- = \widehat{\jmath}_x - i\widehat{\jmath}_y
$$

There are noticable commutation relations involving the $\widehat{\jmath_+}$ and $\widehat{\jmath_-}$ ladder operators:
$$
[\widehat{\jmath}_z, \widehat{\jmath} _{\pm}] = \pm \jmath _{\pm} \\\\
[\widehat{\jmath} _{\+}, \widehat{\jmath} _{\-}] = 2\hbar \jmath_z
$$
, and the action to the angular state
$$
\widehat{\jmath} _{\+} \ket{\jmath m} = \sqrt{\jmath(\jmath+1)-m(m+1)}\ket{\jmath \\;(m+1)} \\\\
\widehat{\jmath} _{\+} \ket{\jmath m} = \sqrt{\jmath(\jmath+1)-m(m-1)}\ket{\jmath \\;(m-1)}
$$

### Specific cases

The reasoning provided is quite general. That is, is valid for any angular momentums. Indeed, in quantum mechanics 
one considers (mainly) 2 types of angular momenta - the __orbital__ angular momentum and __spin__ angular momentum. 
In addition, one can add those two, yielding the __total__ angular momentum.

- __The orbital angular momentum__, (instead of the mentioned $\widehat{\jmath}$ ) denoted $\widehat{L}$ is an analogy to the classical 
angular momentum, taking __integer__ values ($L\equiv 0,1,2...$). It is defined to be 
$$
\widehat{\vec{L}} \coloneqq \widehat{\vec{r}} \times \widehat{\vec{p}}
$$


- __The spin angular momentum__ (instead of the mentioned $\widehat{\jmath}$) denoted $\widehat{S}$ is an 
intrinsic property of a quantum particle, e.g. electron. It takes __half integer__ values.

- __The total angular momentum__ is the angular momentum, obtained by summing the previously mentioned angular and spin 
angular momenta. The sum, however, is not performed in the classical manner. Namely, one cannot simply add them as vectors. 
This notion is reffered to as the _angular momenta addition_ $\widehat{\vec{J}} = \widehat{\vec{L}} + \widehat{\vec{S}}$.

Therefore, for the specific cases, of $L$, $S$ and $J$, one can write 
$$
\widehat{\vec{L}}^2 \ket{lm_l} = l(l+1) \ket{lm_l} \qquad \\& \qquad \widehat{L}\ket{lm_l} = m_l\ket{lm_l} \\\\
\widehat{\vec{S}}^2 \ket{sm_s} = s(s+1) \ket{sm_s} \qquad \\& \qquad \widehat{S}\ket{sm_s} = m_s\ket{sm_s} \\\\
\widehat{\vec{J}}^2 \ket{jm_j} = j(j+1) \ket{jm_j} \qquad \\& \qquad \widehat{J}\ket{jm_j} = m_j\ket{jm_j} 
$$















