# Bidirectional Reflectance Distribution Function (BRDF)

- Describes the reflection behavior of materials 
- Influence of surface structures that are not described geometrically
$$f_r(\omega_i, x, \omega_o) = \frac{dL_o(x, \omega_o)}{L_i(x, \omega_i) cos(\theta_i)d\omega_i}\ [sr^{-1}]$$

- The directions $\omega_i, \omega_o$ can be described via 2 polar angles
- Based on [[Radiometry|radiometric]] quantities and is the ratio between the incident irradiance from direction $l$ and the outgoing radiance in direction $v$

- <mark style="background: #FFB86CA6;">Anisotropic BRDF</mark> - Reflection depends on the rotation around the normal (4 dimensions and the point $x$)
- <mark style="background: #FFB86CA6;">Isotropic BRDF</mark> - Rotational invariance around the normal (3 dimensions and the point $x$)

- <mark style="background: #FFB86CA6;">Anisotrope BRDF</mark> - Reflexion ist abhängig von der Rotation um die Normale (4 Dimensionen und der Punkt $x$)
- <mark style="background: #FFB86CA6;">Isotrope BRDF</mark> - Rotationsinvarianz um die Normale (3 Dimensionen und der Punkt $x$)
- ![[Pasted image 20241112124149.png |400]]

- phänomenologische/empirische Modelle
	- intuitiv verständliche Parameter
	- keine physikalischen Gesetzmäßigkeiten
	- zum Beispiel [[Phong-Beleuchtungsmodell]]
- physikalisch-basierte Modelle
	- Bildet reale Materialien nach
	- Microfacettenmodelle

## Physikalisch plausible BRDFs

Eigenschaften:
- Nicht-negativ:
	- $$f_r(\omega_i, x, \omega_o)\in[0; \infty)$$
	- $0$ bei totaler Absorption, $\infty$ bei perfekter Spiegelung
- Helmholtz-Reziprozität (Umkehrbarkeit des Lichtwegs)
	- $$f_r(\omega_i, x, \omega_o) = f_(\omega_0, x, \omega_i)$$
- Energieerhaltung
	- $$\int_{\Omega^+} f_r(\omega_i, x, \omega_o)\ cos\theta\ dw_o \leq 1\ \forall x, \omega_i$$


---

Origin: Computergrafik
References: [[Raytracing]]
Tags: #🇩🇪 
Created: 07.11.2024

