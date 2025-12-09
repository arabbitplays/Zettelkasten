# Bidirectional Scattering Distribution Function (BSDF)

## Introduction

- Describes the scattering behavior of materials 
	- if the material only reflects, its a <mark style="background: #FFB86CA6;">bidirectional reflection distribution function (BRDF)</mark>
	- if the material only transmits, its a <mark style="background: #FFB86CA6;">bidirectional transmission distribution function (BTDF)</mark>
- Based on [[Radiometry|radiometric]] quantities and is the ratio between the incident irradiance from direction $\omega_i$ and the outgoing radiance in direction $\omega_o$
- Influence of surface structures that are not described geometrically
$$f_r(\omega_i, x, \omega_o) = \frac{dL_o(x, \omega_o)}{L_i(x, \omega_i) cos(\theta_i)d\omega_i}\ [sr^{-1}]$$

## Parameters

- The directions $\omega_i, \omega_o$ can be described via 2 polar angles
- <mark style="background: #FFB86CA6;">Anisotropic BRDF</mark> - Reflection depends on the rotation around the normal (4 dimensions and the point $x$)
	- they require a full [[Tangentspace | tangent frame]], not just the normal of a point
- <mark style="background: #FFB86CA6;">Isotropic BRDF</mark> - Rotational invariance around the normal (3 dimensions and the point $x$)

- ![[Pasted image 20241112124149.png |400]]


## Properties

- soft-skills of a BSDF
	- can be evaluated in closed form and noise free
	- can be [[Importance Sampling | importance sampled]] efficiently
		- must be able to evaluate the PDF for the importance sampling
### Physically plausible BRDFs

- hard properties:
	- Non-negative:
		- $$f_r(\omega_i, x, \omega_o)\in[0; \infty)$$
	- $0$ for total absorption, $\infty$ for perfect reflection
	- Helmholtz reciprocity (reversibility of the light path)
		- $$f_r(\omega_i, x, \omega_o) = f_(\omega_0, x, \omega_i)$$
	- conservation of energy
		- $$\int_{\Omega^+} f_r(\omega_i, x, \omega_o)\ cos\theta\ dw_o \leq 1\ \forall x, \omega_i$$
## Common BSDFs

- perfectly smooth surface -> perfect mirror
$$f_r = \frac{1}{cos \theta_i}\delta(\omega_i-\omega_r),\ \omega_r = 2\langle\omega_o,n\rangle n - \omega_o$$
- [[Lambert Diffuse]]


---

Origin: Computergrafik
References: [[Raytracing]]
Tags: 
Created: 07.11.2024

