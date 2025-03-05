# Importance Sampling

- The variance of a [[Monte Carlo Integration | Monte Carlo sampler]] is reduces if the samples PDF resembles the integrant
- in the context of path tracing, the integrant is $f(\omega_i, p, \omega_o)L_i(p, \omega_i)cos(\theta)$

## BSDF Importance Sampling

- Choose the direction to continue the path not uniformly but by a PDF that resembles the value of the [[Bidirectional Reflectance Distribution Function (BRDF) | BRDF]] in this direction
	- ergo the PDF resembles the $f(\omega_i, p, \omega_o)$ term of the integrant
- Such sampling techniques exist for most common BSDFs (see [[Rough Conductor BRDF]])

## Light Importance Sampling

- <mark style="background: #FFB86CA6;">direct light sampling</mark> means that additional to the normal path (estimating the indirect light to the given point), the direct light to this point is estimated too
	- don't add the emitted light term when hitting a light source by chance
- for direct light sampling, the direction is chosen in the direction of a light
	- ergo the PDF resembles the $L_i(p, \omega_i)$ term of the integrant
- with a chance, send a shadow ray directly to a random point in a random light source


---

Origin: 
References: [[Raytracing]], [[Bidirectional Reflectance Distribution Function (BRDF)]], [[Rough Conductor BRDF]]
Tags: 
Created: 20.02.2025

