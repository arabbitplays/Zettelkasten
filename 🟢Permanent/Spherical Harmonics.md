# Spherical Harmonics

## Introduction

- an orthonormal basis for spherical functions
- they are structured in bands
	- higher bands result in more detailed functions (higher frequencies), but bigger coefficient vectors
- coefficients $f_i$ can be calculated with [[Monte Carlo Integration]] 
$$f_i = \int_\Omega f(\omega)y_i(\omega)d\omega \approx \frac{4 \pi}{N}\sum_j f(\omega_j)y_i(\omega_j)$$
## Properties

- coefficients can most of the time be interpolated and the results are plausible
- simplifies the calculation of integrals of function products
	- just multiply the coefficient vectors of the two functions
$$\int_\Omega a^*(\omega)b^*(\omega) = \sum a_i b_i$$

## Problems

- for high frequent functions, the numerical projection can resulting in too high results for the coefficients of high bands (<mark style="background: #FFB86CA6;">Gibbsches Phänomenon</mark>)
	- reduce the influence of higher bands

---

Origin: 
References: [[Precomputed Radiance Transfer]]
Tags: 
Created: 10.07.2025

