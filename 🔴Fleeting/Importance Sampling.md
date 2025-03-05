# Importance Sampling

- The variance of a [[Monte Carlo Integration | Monte Carlo sampler]] is reduces if the samples PDF resembles the integrant
 
## BSDF Importance Sampling

- Choose the direction to continue the path not uniformly but by a PDF that resembles the value of the [[]] in this direction
	- ergo the PDF resembles the $f(\omega_i, p, \omega_o)$ term of the integrant $f(\omega_i, p, \omega_o)L_i(p, \omega_i)cos(\theta)$
- Such sampling techniques exist for most common BSD

---

Origin: 
References: [[Raytracing]], [[Bidirectional Reflectance Distribution Function (BRDF)]], [[Rough Conductor BRDF]]
Tags: 
Created: 20.02.2025

