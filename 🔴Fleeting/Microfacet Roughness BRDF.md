# Microfacet Roughness BRDF

## Trowbridge-Reitz  Distribution

- $D(\omega_m)$ is the <mark style="background: #FFB86CA6;">distribution function</mark> - the probability of a microfacet having its normal into the given direction
	- if both alphas are the same, the brdf is isotropic
$$D(\omega_m)= \frac{1}{\pi \alpha_x \alpha_y cos^4 \theta_m (1+tan^2 \theta_m(\frac{cos^2\phi_m}{\alpha_x^2} + \frac{sin^2\phi_m}{\alpha_y^2}))^2}$$

- $G_1(\omega, \omega_m)$ is the <mark style="background: #FFB86CA6;">masking function</mark> - the fraction of microfacets with normal $\omega_m$ that are visible from $\omega$

- $D$ and $G_1$ must follow a constraint to be physical plausible, but $D$ defines and infinte set of functions for $G_1$ that follow the constraint 
	- make approximation that heights and normals of the microfacets are statisticaly independend -> surface is not connected anymore but a soup of floating facets
	- the masking function is now independend of $\omega_m$ and the constraint has an analytical solution for the Throwbridge-Reitz Distribution
$$G_1(w_m)=\frac{1}{1+\Lambda(\omega)}$$
$$\Lambda(\omega) = \frac{\sqrt{1+\alpha²tan²\theta}-1}{2}$$
(this is the isotropic case so $\alpha = \alpha_x = \alpha_y$)

- $G($

---

Origin: 
References: 
Tags: 
Created: 20.02.2025

