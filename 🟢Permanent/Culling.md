# Culling

## Introduction

- rendering complicated scenes by removing geometry that is not seen anyway
- <mark style="background: #FFB86CA6;">Backface culling</mark> 
	- remove triangles that face away from the camera
	- is trivial and done by OpenGL
- [[Frustum Culling]]
	- remove triangle outside the view frustum
- [[Occlusion Culling]] 
	- remove occluded triangles
- pay attention when reflection or indirect light is rendered, because then these tests are not necessarily valid anymore

---

Origin: 
References: [[Rendering Index]]
Tags: 
Created: 04.10.2025

