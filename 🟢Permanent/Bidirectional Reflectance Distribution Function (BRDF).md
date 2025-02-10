# Bidirectional Reflectance Distribution Function (BRDF)

- Beschreibt Reflektionsverhalten von Materialien 
	- Einfluss von Oberflächenstrukturen die nicht geometrische beschrieben sind
$$f_r(\omega_i, x, \omega_o) = \frac{dL_o(x, \omega_o)}{L_i(x, \omega_i) cos(\theta_i)d\omega_i}\ [sr^{-1}]$$

- Die Richtungen $\omega_i, \omega_o$ können über 2 Polarwinkel beschrieben werden
- Basiert auf [[Radiometry|radiometrischen]] Größen und ist Verhältnis zwischen der einfallenden Irradiance aus Richtung $l$ und der ausgehenden Radiance in Richtung $v$

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
References: [[💡Resources/📦Zettelkasten/🟢Permanent/Raytracing]]
Tags: 
Created: 07.11.2024

