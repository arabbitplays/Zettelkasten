# GPU Computing History

## Introduction

- GPU computing evolved from single purpose graphics pipelines to general purpose accelerators 

## Classic graphics pipeline

- running code on a GPU consisted of the following steps
	1. application provides shader code to the GPU
	2. application configures parameters of the pipeline 
	3. application provides a buffer with vertices (and textures)
	4. application sends a draw command
- even with this limited interface, general purpose computing could be done one the GPU
	- render screen sized triangle
	- let fragment shader do to computing

## Compute mode interface

- in 2007, Nvidia released the Tesla architecture, the first GPU architecture with a compute mode interface
	1. application allocated buffers in GPU memory and copies data from/to those buffers
	2. application provides a single kernel program binary
	3. application tells GPU to run the program in a [[Flynn's Taxonomy | SPMD]] fashion with $N$ instances
- also the [[CUDA Introduction | CUDA]] language has been introduced
- Vulkan Compute followed in 2016 as a platform independent alternative
	- used SPIR-V and GLSL on the GPU side


---

Origin: 
References: 
Tags: 
Created: 16.09.2025

