# Occlusion Culling

## Introduction

- Remove occluded triangles when rendering a big scene
- can be done from a point or from an area
	- ![[Pasted image 20251004121243.png | 400]]
	- result is longer valid when the camera is moving
- do tests conservativ, as it is better to draw something that is not visible then the other way around

## Occlusion Queries

- hardware solution -> <mark style="background: #FFB86CA6;">occlusion query</mark> return how many fragments of an object pass the depth test
1. Draw simple bounding volumes of objects from front to back
2. For each new volume, check the occlusion query and only draw it if one fragment is visible
- the async nature of GPUs can drive the latency way up here

## Portal Culling

- technique for closed rooms, facilities and buildings
- structure scene into <mark style="background: #FFB86CA6;">cells</mark> (rooms) and <mark style="background: #FFB86CA6;">portals</mark> (doors, windows, mirrors)
	- often manual, but also possible with the Watershed Transformation (Volumetric cell-and-portal generation, Haumont et al.)
- <mark style="background: #FFB86CA6;">Potentially Visible Set (PVS)</mark> - precalculate, which cells can be seen from each cell
	- conservative criteria and thus exact result is really hard
	- test visibility between portals of two rooms
	- makes drawing very easy, as you can just draw the PVS of the current cell
- can also be used without precalculation, by just testing if a portal to another cell is visible
	- Option 1: Calculate view frustum through a portal, check if other portals are in this frustum
		- can be hard if the shape of portals is weird
	- Option 2: Draw portal as a simple test shape and use occlusion queries
		- can be slow if a lot of tests have to be done after each other
---

Origin: 
References: [[Culling]]
Tags: 
Created: 04.10.2025

