# User-Mode Graphics Driver (UMD)

- The layer under graphics APIs like [[Vulkan Index | Vulkan]] 
- runs in user mode without any elevated privileges
	- only crashes the app and not the system
	- can be debugged with normal debuggers 
	- so as much processing as possible is done here
- UMDs wirklich like normal programms on the CPU and the GPU pipeline is a shared Ressource too -> [[Scheduling]]
## Shader Compilation

- gets a precompiled syntacticaly token stream 
	- this stream has high level optimizations applied
- applies low level optimizations and fit jt to hardware requirements 
- this often only happens when the shader is used the first time 

## Memory Allocation

- allocates memory pages from the [[Kernel-Mode Graphics Driver (KMD) | KMD]] and suballocates them for textures and buffers

---

Origin: https://fgiesen.wordpress.com/2011/07/01/a-trip-through-the-graphics-pipeline-2011-part-1/
References: [[Graphics Pipelines Implemented by GPUs]]
Tags: 
Created: 02.10.2024

