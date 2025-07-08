# Precomputed Radiance Transfer

## Introduction

- realtime rendering technique, precomputing how incident light gets turned into reflected light
- incident light is often given by an [[Environment Maps]]
	-  but reflected light depends on the [[Bidirectional Reflectance Distribution Function (BRDF) | BRDF]] and the surrounding geometry (visiblity)  
- represent spherical functions in regards to $m$ orthonormal basis functions $y_k(\omega)$

## Example

- assumes a diffuse BRDF $f(\omega_i, x, \omega_o) = k_d(x)$
- in this scenario, the geometry has to be static after the precomputation
### Precomputation

- <mark style="background: #FFB86CA6;">Transfer function</mark> describes how light from a direction $\omega_i$ contributes to the brightness of a point $x$
- can contain vissiblity for example or even indirect light
$$V(x, \omega_i)max(0, cos\ \theta_i)$$
- approximate the transfer function of every vertex with the basis functions and [[Monte Carlo Integration]] 
	- dot product between functions is defined as $f \cdot g = \int_a^b f(x)g(x)dx$
$$t_{x,k} = T_x \cdot y_k \approx \frac{2 \pi}{N}\sum_i^N T_x(\omega_i)y_k(\omega_i)$$
- store the coefficients vector $\{t_{x,k}\}$ for every vertex

### Runtime Computation

- project environment map onto the basis function -> coefficients $\{l_{k}\}$
- approximate reflected light with
$$L_r(x) = k_d(x) = \int_0^{2\pi}T_x(\omega_i)L(\omega_i)d\omega_i \approx k_d(x) \sum_i^m t_{x,i}l_i$$

## Basis Functions

- most often used: Spherical harmonics
- structured in multiple bands -> more bands give better results but need more memory

---

Origin: 
References: 
Tags: 
Created: 08.07.2025

