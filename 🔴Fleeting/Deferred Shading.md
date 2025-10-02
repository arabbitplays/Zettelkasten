# Deferred Shading

## Introduction

- split rendering process in two phases
	- <mark style="background: #FFB86CA6;">geometry pass</mark> -> collect information of the geometry (position, normal, material) for every pixel
	- <mark style="background: #FFB86CA6;">shading pass</mark> -> use the information to shade every pixel, independent of the geometry

- faster if shading is very expensive (complex materials, many lights, ...)
- needs a lot of memory bandwidth and complex materials can cause problems


## Geometry Pass

- rasterize the whole scene and store data important for shading in the [[G-Buffer]] 
## Shading Pass

- needed to run a fragment shader for every pixel for every light
	- the results are then blended
- to achieve this, render a screenfilling triangle for every light
	- optimization: render a simple bounding volume of the area of influence of a light
		- depth tests skips surfaces that are before the light

- Shading pass creates a triangle for every light 
	- blend them for the final result
	- make triangle only as big as its influence is (avoids screen filling triangle for every light)

## Transparency

- with the basic tools of deferred shading not possible, as only information of first surface is collected in the geometry pass
- transparent objects could be rendered like normal with blending -> expensive when deferred shading is already needed for normal geometry
- in theory, G-Buffers could hold multiple layers -> very memory inefficient if done naive
- <mark style="background: #FFB86CA6;">dpeth-peeling</mark>
	- multiple passes, where in every pass only fragments are used that have a greater depth than the current depth buffer
	- so geometry is rendered layer for layer
- <mark style="background: #FFB86CA6;">per-pixel linked-list</mark>
	- more efficient for high depth complexity
	- store fragments in a node buffer, even if they are behind each other
	- for every pixel, store a pointer to the head of the list (into the node buffer=)

---

Origin: 
References: 
Tags: 
Created: 05.06.2025

