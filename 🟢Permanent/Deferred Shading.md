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

### Tiled Shading

- makes shading for loads of light sources faster by reducing the number of G-Buffer accesses
- view frustum is split into cells (tiling the screen space + depth of the frustum)
- match light sources to the tiles they have influence in
- for every tile, load relevant part of the G-buffer and iterate over the light sources that influence the tile

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
	- for every pixel, store a pointer to the head of the list (into the node buffer)

## Anti-Aliasing

- normal GPU [[Anti Aliasing]] doesn't work on the G-Buffer as interpolated depth, material ID, ... make no senses
- naive approach: generate bigger G-buffer by super sampling in the geometry pass
- <mark style="background: #FFB86CA6;">Morphological Antialiasing (MLAA)</mark> 
	- detect edges through differences is depth, normal or material ID, and blur the edges
	- only fights the artifacts, not prevents them
- [[Temporal Antialiasing (TAA)]]

---

Origin: 
References: 
Tags: 
Created: 05.06.2025

