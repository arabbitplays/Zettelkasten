# Precomputed Radiance Transfer

## Introduction

- realtime rendering technique, precomputing how incident light gets turned into reflected light
- incident light is often given by an [[Environment Maps]]
	-  but reflected light depends on the [[Bidirectional Reflectance Distribution Function (BRDF) | BRDF]] and the surrounding geometry (visiblity)  
- represent spherical functions in regards to $m$ orthonormal basis functions $y_k(\omega)$ (most of the time [[Spherical Harmonics]])

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
	- they describe how much light is reflected from a direction interval at the point $x$

### Runtime Computation

- project environment map onto the basis function -> coefficients $\{l_{k}\}$
	- they describe how much light arrives from a direction interval
- approximate reflected light with
$$L_r(x) = k_d(x) = \int_0^{2\pi}T_x(\omega_i)L(\omega_i)d\omega_i \approx k_d(x) \sum_i^m t_{x,i}l_i$$

## Problems

- <mark style="background: #FFB86CA6;">Ringing</mark> - spherical harmonics only approximate hard edges, and they tend to overshoot around such an edge
	- solution: <mark style="background: #FFB86CA6;">windowing</mark>, where the influence of higher order bands is reduced, to hide these artifacts
## Extensions

1. local lights, not only environment maps
	- calculate SH-coefficients for different light directions
	- with a given light position -> interpolate coefficients to achieve the specific direction (see [[Spherical Harmonics#Properties]])
2. Multiple reflektions in transfer function
3. Specular [[Bidirectional Reflectance Distribution Function (BRDF) | BRDF]]
	- discretize reflection directions, calculate multiple coefficient vectors for these directions, interpolate later
---

Origin: 
References: [[Spherical Harmonics]]
Tags: 
Created: 08.07.2025

