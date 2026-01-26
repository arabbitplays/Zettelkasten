# Next Event Estimation (NEE)

## Introduction

- a way to better find small light sources (and end paths on them) in [[Path Tracing]]
- basic idea: for every vertex sample a point on a light source and send a shadow ray

## Split into direct and indirect illumination

- the [[Rendering Equation]] can be split into a direct and an indirect part
$$L(x, \omega) = L_e(x, \omega) + \int_\Omega f_r(\omega, x, \omega_i) L_e(y, -\omega_i)cos(\theta_i)d\omega_i + \int_\Omega f_r(\omega, x, \omega_i) L_r(y, -\omega_i)cos(\theta_i)d\omega_i = L_e(x, \omega) + L_{direct}(x, \omega) + L_{indirect}(x, \omega)$$
$$L_r(x, \omega) = \int_\Omega f_r(\omega, x, \omega_i) L(y, \omega_i)cos(\theta_i)d\omega_i$$
- at every path vertex $x$
	- evaluate emission
	- compute direct illumination through shadow rays
	- compute indirect illumination through recursion (ignore direct light sources)
- ![[Pasted image 20260123100203.png]]
## Sampling a light source

- pick a vertex $y$ uniformly on a emitting triangle
$$p(y) = 1 / |A|$$
- pick a emitting triangle either uniformly or by flux
$$P(i)=1 / M,\ P(i) = \Phi_i / \Phi_{total}$$
- combined vertex area [[Measure and Measure Space | measure]]
$$p(y) = P(i) \frac{1}{|A|}$$
- because this is vertex area measure, we need the Jacobian from $d\omega^\bot$ to $dx$
- so we get this single sample estimator
$$L_{direct}(x, \omega) \approx \frac{f_r(\omega, x, \omega_i) L_e(y, -\omega_i) G(x, y) V(x, y)}{p(y)}$$

---

Origin: 
References: 
Tags: 
Created: 22.01.2026

