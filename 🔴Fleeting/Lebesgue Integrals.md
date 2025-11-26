# Lebesgue Integrals

## Introduction

- integration method building on [[Measure and Measure Space | Measures]] 
- more general then Riemann Integrals
	- Riemann cuts the x-axis into equally sized parts, and sums up the boxes this creates
	- Lebesgue can cut differently wide boxes and can even have gaps
![[Pasted image 20251121194016.png]]

## Definition

- the integrals are defined on a measure space $(\Omega, \Sigma, \mu)$ 
- first, the integral will be defined over a class of simple functions $g\in\mathcal{S}$ 
	- they are piecewise constant functions $g: \Omega \rightarrow \mathbb{R}$ 
- partition the domain in $A_i \in \Sigma$ and define $a_i \geq 0$ such that
	- $\mathbf{1}_{A}(x) = \{1\ if\ x\in A,\ 0\ otherwise \}$
$$g = \sum_{i=1}^n a_i\cdot \mathbf{1}_{A_i}$$
- then the integral for simple functions is defined as 
$$\int g d\mu =  \mu(g)=\sum_i a_i\mu(A_i)$$
- now the integral can be defined for other functions on $\Omega$ as
$$\int fd\mu = \mu(f) = sup_g\{\mu(g): g \leq f, g \in \mathcal{S}\}$$

### Null Sets

- for the definition of null sets see [[Measure and Measure Space#Definition | here]]
- they are just ignored as the measure returns $0$ so they contribute nothing to the integral

### Dirac Deltas

- they can be integrated through a (zero-centered) Dirac delta measure
$$\delta(A) =
\begin{cases}
0, \text{ if } 0\notin A\\
1, \text{ if } 0\in A
\end{cases}$$
- this works, but with a trick to change the integrant with a Dirac delta function instead of the Dirac delta measure, we get
	- notice that the used $\delta_\mu$ depends on the general measure $\mu$ 
$$\int f(x) d\delta (x) = \int f(x) \delta_\mu(x) d\mu (x) = f(0)$$

## Expectations

- the basic probabilistic definition of expectations is
$$\mathbb{E}(X) = \int_\Omega X p(x)dx$$
- this can be expressed more elegantly with Lebesgue integrals and measures
	- we start with a probabilistic measure space $(\Omega, \sigma, \mathbb{P})$ and a random variable $X:\Omega \rightarrow \mathbb{R}$ 
	- there is a difference between [[Measure and Measure Space#Definition | measuring a set]] $\mathbb{P}(A \subset \Omega)$ and [[Lebesgue Integrals#Definition | measuring a function]] $\mathbb{P}(X)$ 
$$\mathbb{E}(X) = \mathbb{P}(X) = \int_\Omega X\ d\mathbb{P}$$
- discrete random variables can be interpreted as a simple functions and thus $d\mathbb{P}$ can easily be evaluated like this (with $\mathbb{P}(A_i) = p_i$ the chance of $X = x_i$)
$$\mathbb{E}(X) = \int_\Omega X\ d\mathbb{P} = \sum x_i \mathbb{P}(A_i)$$
- in the continuous case we don't know how to evaluate $d\mathbb{P}$ for a general measure
	- only for the Lebesgue measure we know that $d\lambda(x) = dx$ so we need to transform $\mathbb{P}$ into $\lambda$
	- Radon-Nixon derivative to the rescure!

### Radon-Nixon derivative
- Radon Nixon needed because we only know how to evaluate $d\lambda(x) = dx$ 

---

Origin: 
References: [[Measure and Measure Space]]
Tags: 
Created: 21.11.2025

