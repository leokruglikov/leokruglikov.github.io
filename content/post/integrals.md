---
title: "List of useful integrals"
date: "2023-05-17T22:33:44+01:00"
draft: true
tags: ["physics"]
katex: true
markup: "mmark" 
showReadingTime: true
toc: true
---

## Statistical physics
In statistical physics, specifically in the replica method, one identifies 
some used integrals

Gaussian distribution:
$$
\frac{1}{\sqrt{\text{det}(A_n - \lambda 1_N)}}\int_{\mathbb{R}^N} \frac{d\vec{x}}{(2\pi)^{N/2}}
e^{-\frac{1}{2}\vec{x}^{\top}(A_N - \lambda 1_N)\vec{x}} = 1
$$
A more generic formula, for $A$ - a symmetric positive-definite matrix, 
$$
\int_{\mathbb{R}^N} e^{-\frac{1}{2}\vec{x}^{\top}A\vec{x} + B^{\top}\vec{x}} d^n x = \sqrt{\frac{(2\pi)^{n}}{\text{det}A}}
e^{\frac{1}{2}B^{\top}A^{-1}B}
$$

