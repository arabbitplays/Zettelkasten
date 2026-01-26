# Light tracing

## Introduction

- caustics are lights effects that are hard to render with normal [[Path Tracing]]
	- BRDF [[Importance Sampling]] is not good at hitting a light source
	- [[Next Event Estimation (NEE)]] fails because the object causing the caustic blocks the shadow ray
- idea: trace starting at the light up to the caustic and connect to the eye via NEE
	- ![[Pasted image 20260123101948.png | 300]]

- Specular - Diffuse - Specular (SDS) paths are still a failure case
	- ![[Pasted image 20260123103723.png | 300]]
- also big scenes, where a lot of the photon paths never get close to the eye

---

Origin: 
References: 
Tags: 
Created: 23.01.2026

