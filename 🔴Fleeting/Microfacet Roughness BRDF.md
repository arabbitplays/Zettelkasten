# Microfacet Roughness BRDF

## Trowbridge-Reitz  Distribution

- $D(\omega_m)$ is the probability of a microfacet having its normal into the given direction
	- if both alphas are the same, the brdf is isotropic
- $G_1(\omega, \omega_m)$ ist the fraction of microfacets with normal $\omega_m$ that are visible from $\omega$

- $D$ and $G_1$ must follow a constraint to be physical plausible, but $D$ defines and infinte set of functions for $G_1$ that follow the constraint 
	- make approximation that heights and normals of the microfacets are statisticaly independend -> surface is not connected anymore but a soup of floating facets
	- the masking function is now independend of $\omega_m$ and the constraint has an analytical solution for the Throwbridge-Reitz Distribution

---

Origin: 
References: 
Tags: 
Created: 20.02.2025

