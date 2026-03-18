# Rendering Participating Media

## Introduction

- participating media are volumetric media, that can not be rendered by only considering the surface
	- for example clouds, smoke, fire, and even media with significant sub surface light transport like skin, milk or marble
- the physics are described by the [[Radiance Transfer Equation]] and [[Path Tracing]] is commonly used to solve it

## Estimating the equation

- additionaly to sampling a new direction to continue the path when hitting a surface, positions on the way to the surface have to be considered
	- this requires [[Distance and Transmittance Sampling]] and the sampling of a [[Phase Function]] in the case of a scattering event
- the full estimator of the [[Radiance Transfer Equation]] is
$$\langle L(x, \omega)\rangle = \frac{T(x,y)}{p(y)} (\mu_a(y) L_e(y, \omega) + \mu_s(y)L_s(y, \omega)) + \frac{T(x,z)}{P(z)}L_o(z, \omega)$$
- the first part of the sum is the light along the ray through the volume
- the second part is the light from a surface interaction or beyond the volume

- practical sampling procedure for a basic volumetric path tracer:
	- when hitting the boundary of a volume
		- don't change the direction
		- only sample a new distance
	- when NOT hitting a new surface in the volume with the sampled distance
		- add emitted light from the volume
		- adjust the beta by the evaluated phase function and the transmittance of the distance traveled $T(x,y)$, and the probability of the distance traveled $p(y)$
		- sample new direction according to the phase function
		- sample new distance
			- adjust beta by the sampling probability
	- when hitting the volume boundary from the inside
		- adjust beta by the transmittance of the distance traveled $T(x,z)$ and the probability of exceeding the distance to $z$ $P(z)$
		- don't change the direction

---

Origin: https://jannovak.info/publications/VolumeSTAR/index.html
References: [[Rendering Index]]
Tags: 
Created: 16.03.2026

