# Bounding Volume Hierarchy (BVH)

- <mark style="background: #FFB86CA6;">Axis-Aligned Bounding Box (AABB) groups multiple primitives together</mark>j
    - Check against the box first, then against the primitives inside the box
    - Hierarchy where boxes are also contained within other boxes
- Check the root box first, and if there is a hit, check the child boxes
	- Test closer boxes first, even if it’s possible that no primitive was hit
	- Do not terminate immediately, as overlapping boxes may cause a rear box to generate the closest hit
- Reduces $O(n)$ intersection tests to $O(\log(n))$ tests
- Fast construction in $O(\log(n))$
- Optimal construction in $O(\log^2(n))$  

---

Origin: 
References: [[Spatial Datastructures]], [[Binary Space Partitioning Tree (BSP)]]
Tags: 
Created: 23.03.2026

