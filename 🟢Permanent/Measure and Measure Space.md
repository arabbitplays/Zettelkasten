# Measure and Measure Space

## Introduction

- measures are a mathematical construct that can be used to define [[Monte Carlo Integration]] and are needed to describe a lot of renderers
	- they make [[Importance Sampling]] and the Jacobi determinants more intuitive
	- and they allow for sampling when the [[Inverse CDF Method]] doesn't work

## Definition

- <mark style="background: #FFB86CA6;">Measure Space</mark> $(\Omega, \Sigma, \mu)$
	- $\Omega$ is a set and the domain we are interested in
	- $\Sigma$ is a $\sigma$-algebra and is a mathematical technicality that is not important here
		- it includes $\Omega$, all unions of its members and all complements
	- $\mu(A)$ is a <mark style="background: #FFB86CA6;">measue</mark> and assigns a non-negative real number to subsets $A \subset \Omega$ 
		- $mu: \Sigma \rightarrow [0, \infty]$
		- $\mu(\emptyset) = 0$
		- $\mu(A \cup B) = \mu(A)+\mu(B) - \mu(A \cap B)$
		- $A \subset B \implies \mu(A) \leq \mu(B)$
		- $\mu(E) = 0$ means $E$ is a <mark style="background: #FFB86CA6;">Null-Set</mark>
			- the notation a.e. means almost everywhere, meaning everywhere except in a null set
![[Pasted image 20251113182324.png]]
- two different angle measures (solid angle and projected solid angle in 2D)

## Important Measures

- the <mark style="background: #FFB86CA6;">Lebesgue measure</mark> is defined on $(\mathbb{R}, \mathcal{B}, \lambda)$ 
	- so it measures sets of intervals on $\mathbb{R}$ by adding their lengths without overlap 
	- $\mathcal{B}$ is just the set of all sets of intervals in $\mathbb{R}$
- the <mark style="background: #FFB86CA6;">area measure</mark> $\mu_A$ measures surface area on geometry and is the product of two Lebesgue measures
- <mark style="background: #FFB86CA6;">solid angle measure</mark> $\mu_\sigma$ measures the [[Solid Angle]] on the unit-sphere as seen from the center
- the <mark style="background: #FFB86CA6;">projected solid angle measure</mark> $\mu_{\sigma^\perp}$ measures the projected solid angle on the unit disc, oriented with the surface normal
- the <mark style="background: #FFB86CA6;">half vector space</mark> $\mu_h$ is the solid angle of the halfway vector $h = \frac{\omega_i+\omega_o}{\|\omega_i+\omega_o\|}$ as [[Bidirectional Reflectance Distribution Function (BRDF) | BRDF]] interaction

## Probability Measures 

- a measure is a <mark style="background: #FFB86CA6;">probability measure</mark> with $\mu(\Omega) = 1$
	- they are often indicated with $\mu = \mathbb{P}$ 
- a <mark style="background: #FFB86CA6;">random variable</mark> is then defined as a  measurable mapping $X:\Omega \rightarrow \mathbb{R}$ 
	- measurable mapping is another technicality regarding $\sigma$-algebras
	- they map into the measurable space $(\mathbb{R}, \mathcal{B})$
- a with this setup, a probability measure for $B \in \mathcal{B}$ can be defined like $\mu(B) := \mathbb{P}(X^{-1}(B))$ 
	- this is called the <mark style="background: #FFB86CA6;">distribution</mark> 
- a <mark style="background: #FFB86CA6;">distribution function</mark> (the CDF) can be defined a $F(x) = \mu((-\infty, x]) = \mathbb{P}(X < x)$  
![[Pasted image 20251121151728.png | 400]]

- with this setup, the uniform distribution can be defined via the Lebesgue measure 
	- $([0, 1], \mathcal{B}(0, 1), \lambda)$ with the random variable $U = id$ and the distribution is $\lambda$ again
![[Pasted image 20251121152407.png | 400]]
- given a distribution function $F$ on $\mathbb{R}$, a random variable with this distribution function can be constructed as following
	- <mark style="background: #D2B3FFA6;">this is a transformation from a uniform variable to one following a specific CDF that does not have to be differentiable</mark> (more general [[Inverse CDF Method]])
$$X⁻(\xi) = inf\{x \in \mathbb{R}: F(x) \geq \xi\}$$

---

Origin: 
References: 
Tags: 
Created: 13.11.2025

