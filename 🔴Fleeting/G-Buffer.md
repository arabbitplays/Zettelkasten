# G-Buffer

## Introduction

- a G-Buffer stores information about the visible geometry in a scene for every pixel
	- position, normal, material parameters, ...
- used for [[Deferred Shading]], [[Denoising]] or other Image Space techniques
- for high resolution images, the memory bandwidth can become a problem

## Optimizations

- reconstruct position from camera projection and depth value
- as normal is a unit vector, it needs only two components saved (see [[Texture Mapping]])
	- for example sphere maps or octahedral maps
- don't save all material parameters, only store an index into the material buffer

---

Origin: 
References: 
Tags: 
Created: 29.09.2025

