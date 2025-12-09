# Importance Sampling

- Variance reduction technique for [[Monte Carlo Integration]]
- The variance of a Monte Carlo Estimator is reduced if the samples PDF resembles the integrand
- in the context of path tracing, the integrand is $f(\omega_i, p, \omega_o)L_i(p, \omega_i)cos(\theta)$

## BSDF Importance Sampling

- Choose the direction to continue the path not uniformly but by a PDF that resembles the value of the [[Bidirectional Scattering Distribution Function (BSDF)| BRDF]] in this direction
	- ergo the PDF resembles the $f(\omega_i, p, \omega_o)$ term of the integrand
- Such sampling techniques exist for most common BSDFs (see [[Rough Conductor BRDF]])

## Light Importance Sampling

- <mark style="background: #FFB86CA6;">direct light sampling</mark> means that additional to the normal path (estimating the indirect light to the given point), the direct light to this point is estimated too
	- <mark style="background: #D2B3FFA6;">don't add the emitted light term when hitting a light source with the normal path</mark>
- for direct light sampling the direction can be chose directly in the direction of a random light
	- ergo the PDF resembles the $L_i(p, \omega_i)$ term of the integrand
	- if it is clear that the ray is always in the direction of a light source, it is enough to send a shadow ray to only check if the direction is occluded
- when using triangle meshes, the direction can be chose by picking a random emitting triangle and then a random point on the triangle to sample from
	- the process of picking a light can be uniform of more sophisticated like sampling by the power of the light
- the sampled direction can additionally be chosen dependent on the BSDF with 

---

Origin: 
References: [[Raytracing]], [[Bidirectional Scattering Distribution Function (BSDF)]], [[Rough Conductor BRDF]]
Tags: 
Created: 20.02.2025

