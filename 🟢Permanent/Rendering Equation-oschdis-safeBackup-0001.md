# Rendering Equation

- $f_r$ ist die [[Bidirectional Reflectance Distribution Function (BRDF) |BRDF]], $\Omega^+$ ist die Hemisphäre um den Punkt $x$
$$L(x, \omega_o) = L_e(x, \omega_o)+\int_{\Omega^+}f_r(\omega_o, x, \omega_i)(n \cdot \omega_i)d\omega_i$$

## Herleitung

Zusammenhänge aus der [[Radiometry]]:
$$dE = L\ cos\theta\ d\omega$$
$$E(x)=\int_{\Omega^+}L_i(x, \omega)\ cos\theta\ d\omega$$
![[Pasted image 20241121155651.png |200]]

Die BRDF $f_r(\omega_i, x, \omega_o)$ beschreibt den Zusammenhang der einfallenden Irradiance zur ausgehenden Radiance
$$f_r(\omega_i, x, \omega_o) = \frac{dL_o(x, \omega_o)}{dE_i(x, \omega_i)} = \frac{dL_o(x, \omega_o)}{L_i(x, \omega_i)\ cos\theta\ d\omega_i}$$
$$dL_o(x, \omega_o) = f_r(\omega_i, x, \omega_o)\ L_i(x, \omega_i)\ cos\theta\ d\omega_i$$
- Integration über die Hemisphäre ergibt den Reflektanzanteil der Rendering Equation
---

Origin: Computergrafik I
References: [[💡Resources/📦Zettelkasten/🟢Permanent/Raytracing]]
Tags: 
Created: 19.11.2024

