# Measure and Measure Space

## Introduction

- measures are a mathematical construct that can be used to define [[Monte Carlo Integration]] and are needed to describe a lot of renderers
	- they make [[Importance Sampling]] and the Jacobi determinants more intuitive
	- and they allow for sampling when the [[Inverse CDF Method]] doesn't work

## Definition

- <mark style="background: #FFB86CA6;">Measure Space</mark> $\Omega, \Sigma, \mu)$
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
- two different angle measures

---

Origin: 
References: 
Tags: 
Created: 13.11.2025

