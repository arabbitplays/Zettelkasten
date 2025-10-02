# Temporal Antialiasing (TAA)

## Introduction

- Instead of sampling multiple positions per frame, sample only one per frame but collect them over time
- reproject fragment with the previous view and projection matrix to the screen position of the last frame
	- if depth, normal, material id, etc. is the same, the sample can be integrated with the other ones
	- these tests should fail if a disocclusion happens
- <mark style="background: #FFB86CA6;">ghosting</mark> is when the history is not valid anymore, but it is not wiped (because the tests are too loose)
	- so "ghost trails" are visible behind moving objects

## Neighborhood Clipping

- calculate neighboring colors in the current frame
	- gives bounding volume of chromas found in this volume
- clip history color into this volume to avoid having too much a difference
![[Pasted image 20251002152059.png | 300]]

---

Origin: 
References: 
Tags: 
Created: 02.10.2025

