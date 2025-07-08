# Signed Distance Field (SDF)

## Introduction

- alternative way to represent geometry in rendering applications
- define an analytical distance function $f(x,y,z) = d$ 
	- points with $d = 0$ are considered the surface of the described object 
	- points with $d < 0$ are inside the object 
- they often have a lot smaller memory footprint then triangle meshes

## Creating complex SDFs

https://iquilezles.org/articles/distfunctions/
- there exist primitive SDFs for base forms like spheres, cubes, torus, etc
- they can be combined through boolean operations like max, min, etc
- or deformed by deformer operations like bends, twists, etc

## Function trees

- they can be considered a tree of functions, evaluated from the bottom to the top until the final distance is outputted by the root node
	- every leaf is a primitive
	- every inner node is either a boolean operation or a deformer
- ![[Pasted image 20250708120826.png | 400]]
- more complex trees can get slow to evaluate

---

Origin: 
References: [[Ray Marching]]
Tags: 
Created: 08.07.2025

