# Appearance Filtering

## Introduction

- reduction of details in the geometry in [[Level-of-Detail]] procedures can change appearance
	- the mean of multiple normals goes against a flat surface
	- correlation between color and normals can get lost
- core problem: shading ($f$) with a lot of normals an then filtering is not the same as [[Texture filtering | filtering]] the normals and calculating the shading
$$1/N \sum f(n_i) \neq f(1/N\sum n_i)$$

## Linear Efficient Antialiased Normal (LEAN) Mapping

- for every texel of the normal map, store the distribution of normals 
	- with a combination of [[von Mises Fisher Distribution]]s
- distributions of multiple texels can be combined
- reconstruct a normal distribution function (after filtering, [[Mipmapping]], etc.) and plug it into a microfacet [[Bidirectional Scattering Distribution Function (BSDF)| BRDF]] like Cook-Torance

---

Origin: 
References: 
Tags: 
Created: 06.10.2025

