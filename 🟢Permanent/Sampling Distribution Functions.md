# Sampling Distribution Functions

## Introduction

In [[Path Tracing]], it is often needed to pick a random direction, or point on the surface, according to a given distribution function.
But pseudo random number generators only produce uniformly distributed random variables $\xi \in [0, 1)$ 

- [[Disk Sampling]]
- [[Triangle Sampling]]
## [[Inverse CDF Method]]

## Rejection Sampling

- given a function $f(x)$ which we want to sample, but where the inversion of the associated CDF is not possible (or some other reason to not use another sampling method)
	- a PDF $p(x)$ with $f(x) < cp(x)$ for some constant $c$ can be used
- draw a sample of $p$ and if it lies inside of $f$ is is returned, else another sample of $p$ is taken
	- for example sample the square uniformly and except if inside the circle to uniformly sample the circle
- efficiency depends on how tight $p$ fits $f$
![[Pasted image 20250730005713.png]]

---

Origin: 
References: 
Tags: 
Created: 20.05.2025

