# Ray Marching

## Introduction

- the idea of stepping along a ray and evaluating a function at each step
- most common application is sphere tracing, but can also be used for volume rendering (for example evaluating a density function)

## Sphere Tracing

- use a [[Signed Distance Field (SDF)]] to describe the geometry of the scene
- when tracing a ray: evaluate $SDF(x,y,z) = d$ and move $d$ units along the ray
	- when $d \rightarrow 0$ the ray has hit a surface
- can do a lot of useless steps if  a surface is missed by a bit (because only small steps are taken there)
#todo add volume rendering and more sphere tracing and everything

---

Origin: 
References: [[Raytracing]]
Tags: 
Created: 08.07.2025

