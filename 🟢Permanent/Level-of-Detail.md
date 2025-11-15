# Level-of-Detail

## Introduction

- draw only what the viewer can see
- <mark style="background: #FFB86CA6;">geometric level-of-detail</mark> - reduce geometric complexity of models 
	- also results in automatic [[Anti Aliasing]]
![[Pasted image 20251004124358.png]]
- to avoid geometric [[Anti Aliasing | Aliasing]], [[Appearance Filtering]] may be needed
## Terrain Rendering

- when a terrain is represented with a height field, the triangle mesh can be adapted to show more of less detail of this height field
- this can be done with [[Concurrent Binary Tree (CBT)]] and Longest Edge Bisection

## Adaptive Geometrysimplification

- three basic operations: vertex, edge and triangle collapse
- pick the element to collapse by minimizing an error metric
	- change of triangle area, or change of curvature, ...
	- these metrics are often only local and thus the shape is not well preserved
- <mark style="background: #FFB86CA6;">Static LOD</mark> - precalculate discrete LOD that can be swapped out depending on the size of the bounding volume on the screen for example
	- simple, no overhead
	- can result in popping artifacts when the model is swapped -> blend over the two meshes
- <mark style="background: #FFB86CA6;">Continuous LOD</mark> - fine adaption of the detail by adding and removing triangles
- There are also some very conservative methods, used to generate occluders for [[Occlusion Culling]]

## Decoupled Geometry

- other representations of the geometry, for example [[Signed Distance Field (SDF)]], sphere cloud or voxel octrees
- voxel octree 
	- progressively split the space and store which nodes are filled
	- ![[Pasted image 20251004132152.png | 400]]
	- one can even only store indices to common patterns (for example for the patterns in the blue layer)

---

Origin: 
References: 
Tags: 
Created: 04.10.2025

