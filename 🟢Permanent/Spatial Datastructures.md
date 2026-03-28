# Spatial Data Structures

- Accelerate ray traversal by reducing ray-triangle intersection tests

## Types
- [[Bounding Volume Hierarchy (BVH)]]
-  [[Binary Space Partitioning Tree (BSP)]]
- Regular grids
	- Division of space into cells of equal size and shape
    - Assigning objects to cells intersected by the ray
    - Traversing the cells intersected by the ray, performing intersection tests with the contained objects
    - <mark style="background: #D2B3FFA6;">Adaptive subdivision of the grid</mark>

		- ![[Pasted image 20241217132504.png |300]]

## Construction

- Start with a large bounding box and recursively divide it into new boxes (for BVHs) or into two sides (for k-d trees)
    - The choice of divisions affects subsequent performance
- Goal:
	- Find compact and densely populated regions
    - Separate sparsely populated regions -> resulting in very small bounding boxes later on

### Spatial Mean

- Split along the axis of the greatest extent
- <mark style="background: #FF5582A6;">Often very unbalanced</mark>
- $O(n\ log(n)$
### Object-based average

- Split so that both child nodes have the same number of primitives
- $O(n\ log^2(n))$
### Surface Area Heuristic

$$C=C_T + P(hit\ L)C(L) + P(hit\ R)C(R)$$
- $C_T$ is the cost of deciding which child node to proceed with
- $P$ is the probability of hitting the left/right child node
    - Let $SA(B)$ be the surface area of a box, then $P(hit\ X) = \frac{SA(B_X)}{SA(B_P)}$
- $C(L), C(R)$ are the costs of traversing the left/right child node
    - usually $primitive cost \times count$ 
- $O(n\ log^2(n))$

---

Origin: 
References: [[Zettelkasten/🟢Permanent/Raytracing|Raytracing]]
Tags: 
Created: 17.12.2024

