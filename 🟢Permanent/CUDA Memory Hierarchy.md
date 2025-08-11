# CUDA Memory Hierarchy

## Introduction

- different layers in the [[CUDA Thread Hierarchy]] have different access to data

- each thread has its own local registers and local memory
- all threads of a block share memory that is visible to all threads and has the same lifetime as the block itself
- all threads have access to the same global memory
- two additional read-only memory spaces:
	- constants memory space
	- texture memory space
		- offers different accessing modes and data filtering ([[Texture filtering]])

## Heterogenous Programming

- the CUDA programming model assumes that the kernels execute on a physical seperate device (the GPU) while the c++ program runs on the host device (the CPU)
- both devices have their own address spaces, called device memory and host memory
- unified memory provides managed memory that is accessible by all CPUs and GPUs from the system

---

Origin: [CUDA C Programming Guide](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html)
References: 
Tags: 
Created: 29.07.2025

