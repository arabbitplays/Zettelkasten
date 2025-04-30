# Radiosity Precomputation
## Introduction

- Solve the [[Rendering Equation]] under some assumptions to get some precomputed indirect lighting
- Only diffuse materials can be modeled and the precomputation saves the radiosity ([[Radiometry]]) for patches of area in the scene

## Derivation

- take the rendering equation with respect to area, assume a diffuse [[Bidirectional Reflectance Distribution Function (BRDF)]] with albedo $\rho(x)$ and replace radiance with radiosity
$$B(x) = B_e(x) + \frac{\rho(x)}{\pi} \int_S B(y)V(x,y)G(x,y)dy$$

- simplify 
	- with new geometry function $G'(x,y) = \frac{V(x,y)G(x,y)}{\pi}$
	- finite element method: assume radiosity (and emissison and reflectivity) is constant over surface patches 
		- area of a patch is $A_i$
		- Radiosity of a patch is average over all points: $B_i = \frac{1}{A_i}\int_{x\in A_i} B(x)dx$
$$B(x) = B_e(x) + \rho(x) \sum_j B_j \int_{y\in A_j} G'(x,y)dy$$
- we're interested in the ave

---

Origin: 
References: 
Tags: 
Created: 30.04.2025

