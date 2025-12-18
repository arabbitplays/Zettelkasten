# Microfacet Models

## Introduction

. microscopic surface of rock, paper and scissors
![[Pasted image 20251211113847.png]]

- materials and their surfaces are modeled as many smooth <mark style="background: #FFB86CA6;">microfacets</mark> 
	- they are big in comparison to light wavelength
	- but too small to be modeled with triangles ->  statistical approach for the [[Bidirectional Scattering Distribution Function (BSDF) | BSDFs]]

- microfacets are often assumed to be perfect mirrors 
	- but other micro BSDFs are possible
![[Pasted image 20251211114044.png | 300]]

- three effects have to be modeled
	- <mark style="background: #FFB86CA6;">shadowing</mark> - incoming light is blocked by the facets
		- ![[Pasted image 20251211114149.png | 300]]
	- <mark style="background: #FFB86CA6;">masking</mark> - outgoing light is blocked by the facets
		- ![[Pasted image 20251211114227.png | 300]]
	- in general there will be multiple scattering between the facets
		- ![[Pasted image 20251211114329.png | 300]]
- this can be modeled statisticaly with
	- a <mark style="background: #FFB86CA6;">normal distribution function (NDF)</mark> $D(\omega)$ 
		- common choices are Beckmann Lobe or GGX (also called Throwbridge/Reitz)
	- a <mark style="background: #FFB86CA6;">shadowing/masking term</mark> $G(.)$ 
		- normally depends on the chosen NDF
	- a parameter $\alpha \in [0, 1]$ describing how rough the surface is (0 is smooth)

- so the final form of the BRDF (when the facets are assumed to be mirrors) is 
$$f_r(\omega,\mathbf{x},\omega_i) = \frac{F(\langle\omega,\omega_h\rangle) D_\alpha(\omega_h) G(\omega,\omega_i,\omega_h)}{4\langle\omega_g,\omega\rangle\langle\omega_g,\omega_i\rangle}$$

- see [[Rough Conductor BRDF]] for more
## Importance Sampling

- the NDF is the most important term here, so normally, the NDF is sampled
	- because of shadow/masking, its better to sample the visible normals, (VNDF sampling)

---

Origin: 
References: 
Tags: 
Created: 11.12.2025

