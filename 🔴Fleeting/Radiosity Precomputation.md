# Radiosity Precomputation
## Introduction

- Solve the [[Rendering Equation]] under some assumptions to get some precomputed indirect lighting
- Only diffuse materials can be modeled and the precomputation saves the radiosity ([[Radiometry]]) for patches of area in the scene

## Derivation

- take the rendering equation with respect to area, assume a diffuse [[Bidirectional Reflectance Distribution Function (BRDF)]] with albedo $\rho(x)$ and replace radiance with radiosity
$$B(x) = B_e(x) + \frac{\rho(x)}{\pi} \int_S B(y)V(x,y)G(x,y)dy$$

- simplify 
	- with new geometry function $G'(x,y) = \frac{V(x,y)G(x,y)}{\pi}$
	- finite element method: assume radiosity (and emissison $E_i$ and reflectivity $\rho_i$) is constant over surface patches 
		- area of a patch is $A_i$
		- Radiosity of a patch is average over all points: $B_i = \frac{1}{A_i}\int_{x\in A_i} B(x)dx$
$$B(x) = B_e(x) + \rho(x) \sum_j B_j \int_{y\in A_j} G'(x,y)dy$$
	- we're interested in the average incoming light vor the patches, so average both sides over $x \in A_i$
$$B_i = E_i + \frac{1}{A_i} \int_x \rho_i \sum_j B_j \int_y G'(x,y)dydy$$
$$B_i = E_i + \rho_i \sum_j B_j \frac{1}{A_i} \int_x \int_y G'(x,y)dydy := E_i + \rho_i \sum_j B_j F_{ij}$$
- The $F_{ij}$ are called <mark style="background: #FFB86CA6;">Form Factors</mark> and give the share of the radiosity $B_j$ that reaches the patch $i$
- $F_{ij} \neq F_{ji}$ but $A_i F_{ij} = A_j F_{ji}$

## Solution Strategies

- assume the $F_{ij}$ are given
- bring the equation $B_i = E_i + \rho_i \sum_j B_j F_{ij}$ into matrix form
![[Pasted image 20250430121118.png]]
$$B = E + TB \implies B = (1-T)^{-1} E$$
- Solve the system (for example invert with Gauss elemination in $O(n^3)$ for $n$ patches) and convert radiosity to radiance with $L_i = B_i / \pi$
	- interpolate patches for smooth results

## Form Factor Calculation

- in almost all cases, they have to be calculated numerically (iterations)
- two basic approaches
	- <mark style="background: #FFB86CA6;">Gathering:</mark> each step gathers radiosity form other patches
	- <mark style="background: #FFB86CA6;">Shooting:</mark> each step finds bright patches and distributes their radiosity to other patches

---

Origin: 
References: 
Tags: 
Created: 30.04.2025

