# Triangle Sampling

## Introduction

The goal is to sample a triangle uniformly.

## Triangle Sampling

- sample points in a parallelepiped  with 
$$a + \xi_1 e_1 + \xi_2 e_2$$
and reject the sample if 
$$\xi_1 + \xi_2 > 1$$
or mirror these points back into the triangle

## Mesh Sampling

- given a whole mesh, first pick a triangle with probability $A_\triangle / A_{total}$
- then sample the triangle uniformly
- <mark style="background: #FF5582A6;">sample can be very close to each other</mark>
	- enforce a minimum distance

---

Origin: 
References: 
Tags: 
Created: 20.05.2025

