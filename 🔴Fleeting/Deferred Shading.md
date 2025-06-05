# Deferred Shading

## Introduction

- split rendering process in two phases
	- geometry pass -> collect information of the geometry (position, normal, material) for every pixel
	- shading pass -> use the information to shade every pixel, independent of the geometry

- faster if shading is very expensive (complex materials, many lights, ...)
- needs a lot of memory and bandwidth

## Implementation

- Geometry pass is relatively normal
- Shading pass creates a triangle for every light 
	- blend them for the final result
	- make triangle only as big as its influence is (avoids screen filling triangle for every light)

---

Origin: 
References: 
Tags: 
Created: 05.06.2025

