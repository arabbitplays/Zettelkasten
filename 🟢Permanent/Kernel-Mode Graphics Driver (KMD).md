# Kernel-Mode Graphics Driver (KMD)

- actually interacts with the hardware 
- only one runs on the GPU, handling memory visualization, GPU setup or the actual consumed command buffer
	- command buffers from the UMD are only memory, and a pointer to them is written to the actual command buffer when the scheduler decides the program may run

---

Origin: https://fgiesen.wordpress.com/2011/07/01/a-trip-through-the-graphics-pipeline-2011-part-1/
References: [[Graphics Pipelines Implemented by GPUs]]
Tags: 
Created: 02.10.2024

