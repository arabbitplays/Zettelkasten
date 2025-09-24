# Radiosity Precomputation
## Introduction

- Solve the [[Rendering Equation]] under some assumptions to get some precomputed indirect lighting
- Only diffuse materials can be modeled and the precomputation saves the radiosity ([[Radiometry]]) for patches of area in the scene

## Derivation

- take the rendering equation with respect to area, assume a diffuse [[Bidirectional Reflectance Distribution Function (BRDF)]] with albedo $\rho(x)$ and replace radiance with radiosity
$$B(x) = B_e(x) + \frac{\rho(x)}{\pi} \int_S B(y)V(x,y)G(x,y)dy$$

- simplify 
	- with new geometry function $G'(x,y) = \frac{V(x,y)G(x,y)}{\pi}$
	- <mark style="background: #FFB86CA6;">finite element method</mark>: assume radiosity (and emissison $E_i$ and reflectivity $\rho_i$) is constant over surface patches 
		- area of a patch is $A_i$
		- Radiosity of a patch is average over all points: $B_i = \frac{1}{A_i}\int_{x\in A_i} B(x)dx$
$$B(x) = B_e(x) + \rho(x) \sum_j B_j \int_{y\in A_j} G'(x,y)dy$$
	- we're interested in the average incoming light for the patches, so average both sides over $x \in A_i$
$$B_i = E_i + \frac{1}{A_i} \int_x \rho_i \sum_j B_j \int_y G'(x,y)dydy$$
$$B_i = E_i + \rho_i \sum_j B_j \frac{1}{A_i} \int_x \int_y G'(x,y)dydy := E_i + \rho_i \sum_j B_j F_{ij}$$
- The $F_{ij}$ are called <mark style="background: #FFB86CA6;">Form Factors</mark> and give the share of the radiosity $B_j$ that reaches the patch $i$
- $F_{ij} \neq F_{ji}$ but $A_i F_{ij} = A_j F_{ji}$

## Solution Strategies

- assume the $F_{ij}$ are given
- bring the equation $B_i = E_i + \rho_i \sum_j B_j F_{ij}$ into matrix form
![[Pasted image 20250430121118.png]]
$$B = E + TB \implies B = (1-T)^{-1} E$$
- Solve the system (for example invert with Gauss elimination in $O(n^3)$ for $n$ patches) and convert radiosity to radiance with $L_i = B_i / \pi$
	- interpolate patches for smooth results
- this is pretty inefficient -> use iterative solution strategies
	- <mark style="background: #FFB86CA6;">gathering</mark> 
		- in each iteration, gather energy from other patches
		- Jacobi or Gauss-Seidel iteration
		- ![[Pasted image 20250917103734.png | 200]]
	- <mark style="background: #FFB86CA6;">shooting</mark>
		- search patches with a lot of energy, and distribute this energy to other patches
		- Southwell iteration or progressive refinement
		- ![[Pasted image 20250917103749.png | 200]]

### Jacobi Iteration

- we want to solve $B = (1-T)^{-1}E \Leftrightarrow KB = E$
- per element formula of the Jacobi iteration (split $K$ into $K=U+D+L$)
$$B_i^{(k+1)} = \frac{1}{K_{ii}} \left( E_i - \sum_{i\neq j} K_{ij} B_j^{(k)} \right)$$
- this needs a ping pong buffer!
- flat surfaces don't transport light to themselfs, so $F_{ii} = 0 \implies K_{ii}=1-\rho_i F_{ii} = 1$ and
$$B_i^{(k+1)} = E_i + \sum_{i\neq j} \rho_i F_{ij} B_j^{(k)} = E_i+TB^{k}$$
- this is exactly one application of the transport operator $T$E_i + T B^{(1)} = E_i + T (E_i + T B^{(0)})
$$\begin{align}
B_i^{(0)} &= E_i\\
B_i^{(1)} &=  E_i + T E_i\\
B_i^{(2)} &= E_i + T E_i + T^2 E_i\\
  \cdots\\
B_i^{(n)} &= \sum_{k=0}^n T^k E_i
\end{align}$$
- and this is exactly the Neumann series

## Form Factor Calculation

- in almost all cases, they have to be calculated numerically 
	- with [[Monte Carlo Integration]] or by iteration

## Mesh Refinement

- as everything builds on the averaging of radiosity over patches (finite element method), the meshing directly influences the result
![[Pasted image 20250917104006.png]]
- there are approaches to hierarchical transport of radiosity or even meshless approaches where only points get placed in the scene

---

Origin: 
References: 
Tags: 
Created: 30.04.2025

