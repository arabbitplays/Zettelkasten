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
- they are invariant for rotations -> its not important if the projected function or the coefficients are rotated
	- matrix $M$ describes how the $i$-th rotated basis function effects the $j$-th basis function
$$f_j = \int_\Omega f(R(\omega))y_j(\omega)d\omega = \int_\Omega \sum_i^{n^2} f_i y_i(R(\omega))y_j(\omega)d\omega = \sum_i^{n^2} f_i\int_\Omega y_i(R(\omega))y_j(\omega)d\omega = \sum_i^{n^2}f_i M_{j,i}$$

## Problems

- for high frequent functions, the numerical projection can resulting in too high results for the coefficients of high bands (<mark style="background: #FFB86CA6;">Gibbsches Phänomenon</mark>)
	- this is because discontinuous functions can not be expressed 
	- reduce the influence of higher bands
![[Pasted image 20251003121700.png | 300]]

---

Origin: 
References: [[Precomputed Radiance Transfer]]
Tags: 
Created: 10.07.2025

