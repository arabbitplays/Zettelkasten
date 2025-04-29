# Rendering Equation

- used to calculate the light a point $x$ emits in the direction $\omega_o$ 
- $f_r$ is the [[Bidirectional Reflectance Distribution Function (BRDF) |BRDF]], $\Omega^+$ is the hemisphere around the point $x$
$$L(x, \omega_o) = L_e(x, \omega_o)+\int_{\Omega^+}f_r(\omega_o, x, \omega_i)(n \cdot \omega_i)d\omega_i$$
- the native space of this equation is [[Solid Angle]]

## With Respect to Area

-  to relate a differential solid angle with a differential patch of area around a visible point $y$
$$d\omega_i = \frac{dy\ cos(\theta_j)}{||x-y||^2}$$
- to get the visiblility, introduce the binary function $V(x,y)$ thats true when $y$ is visible from $x$
$$L(x, \omega_o) = L_e(x, \omega_o)+\int_{S}f_r(\omega_o, x, \omega_i)V(x,y)d\omega_i$$
## Derivation from Radiometry

Equations from [[Radiometry]]:
$$dE = L\ cos\theta\ d\omega$$
$$E(x)=\int_{\Omega^+}L_i(x, \omega)\ cos\theta\ d\omega$$
![[Pasted image 20241121155651.png |200]]

The BRDF $f_r(\omega_i, x, \omega_o)$ describes the relationship between the incoming Irradiance and the outgoing radiance 
$$f_r(\omega_i, x, \omega_o) = \frac{dL_o(x, \omega_o)}{dE_i(x, \omega_i)} = \frac{dL_o(x, \omega_o)}{L_i(x, \omega_i)\ cos\theta\ d\omega_i}$$
$$dL_o(x, \omega_o) = f_r(\omega_i, x, \omega_o)\ L_i(x, \omega_i)\ cos\theta\ d\omega_i$$
- Integration over the hemisphere resukts in the reflactance part of the rendering equation.
---

Origin: Computergrafik I
References: [[💡Resources/📦Zettelkasten/🟢Permanent/Raytracing]]
Tags: 
Created: 19.11.2024

