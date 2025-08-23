# Bidirectional Reflectance Distribution Function (BRDF)

- Describes the reflection behavior of materials 
- Influence of surface structures that are not described geometrically
$$f_r(\omega_i, x, \omega_o) = \frac{dL_o(x, \omega_o)}{L_i(x, \omega_i) cos(\theta_i)d\omega_i}\ [sr^{-1}]$$

- The directions $\omega_i, \omega_o$ can be described via 2 polar angles
- Based on [[Radiometry|radiometric]] quantities and is the ratio between the incident irradiance from direction $l$ and the outgoing radiance in direction $v$
- Most simple one is the Lambertian diffuse, the diffuse component of the [[Phong Lighting Model]]

- <mark style="background: #FFB86CA6;">Anisotropic BRDF</mark> - Reflection depends on the rotation around the normal (4 dimensions and the point $x$)
- <mark style="background: #FFB86CA6;">Isotropic BRDF</mark> - Rotational invariance around the normal (3 dimensions and the point $x$)

- ![[Pasted image 20241112124149.png |400]]

- phenomenological/empirical models
- intuitively understandable parameters
- no physical laws
- for example [[Phong illumination model]]
- Physics-based models
- Forms real materials according to
- Microfacet models

## Physically plausible BRDFs

Properties:
- Non-negative:
	- $$f_r(\omega_i, x, \omega_o)\in[0; \infty)$$
- $0$ for total absorption, $\infty$ for perfect reflection
- Helmholtz reciprocity (reversibility of the light path)
- $$f_r(\omega_i, x, \omega_o) = f_(\omega_0, x, \omega_i)$$
- conservation of energy
- $$\int_{\Omega^+} f_r(\omega_i, x, \omega_o)\ cos\theta\ dw_o \leq 1\ \forall x, \omega_i$$

---

Origin: Computergrafik
References: [[Raytracing]]
Tags: 
Created: 07.11.2024

