# Radiosity Precomputation
## Introduction

- Solve the [[Rendering Equation]] under some assumptions to get some precomputed indirect lighting
- Only diffuse materials can be modeled and the precomputation saves the radiosity ([[Radiometry]]) for patches of area in the scene

## Derivation

- take the rendering equation with respect to area, assume a diffuse [[Bidirectional Reflectance Distribution Function (BRDF)]] with albedo $\rho(x)$ and replace radiance with radiosity
$$B(x) = B_e(x) + \frac{\rho(x)}{\pi} \int_S B(y)V(x,y)G(x,y)dy$$

- simplify 
	- with new geometry function $G'(x,y) = \frac{V(x,y)G(x,y)}{\pi}$
	- 

---

Origin: 
References: 
Tags: 
Created: 30.04.2025

