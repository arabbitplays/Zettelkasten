# Vulkan Memory Management

## Heap Selection

- not all drivers expose all kinds of flag combinations

- `VK_MEMORY_PROPERTY_DEVICE_LOCAL_BIT` - GPU memory not visible to the CPU
	- fastest one to access from the GPU
	- use to store GPU only data (compute buffers), render targets and static resources like texture or geometry buffers
- `VK_MEMORY_PROPERTY_DEVICE_LOCAL_BIT | VK_MEMORY_PROPERTY_HOST_VISIBLE_BIT` - video memory that the CPU can write to directly
	- normally pretty small but fast to access for both
	- used for data that is updated every frame like uniform buffers or dynamic geometry buffers
- `VK_MEMORY_PROPERTY_HOST_VISIBLE_BIT | VK_MEMORY_PROPERTY_HOST_COHERENT_BIT` - CPU memory that is visible from the GPU
	- reads go over the PCI-express
	- in absence of the previous type used for uniform buffers or dynamic geometry buffers
	- also used for staging buffers to get memory to GPU local memory

## Suballocation

- having many small allocations can be slow and drivers are only required to support 4096 single allocations
- a typical pattern is to allocate a bigger chunk of memory with `vkAllocateMemory` and then suballocating it for single resources
	- application must handle alignment 

---

Origin: https://zeux.io/2020/02/27/writing-an-efficient-vulkan-renderer/
References: 
Tags: 
Created: 12.02.2025

