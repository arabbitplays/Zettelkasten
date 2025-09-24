
# Vulkan Index

- Basics
	- [[Important Vulkan Objects]]
	- [[Important Vulkan Extensions]]
- Efficiency
	-  [Writing an Efficient Vulkan Renderer](https://zeux.io/2020/02/27/writing-an-efficient-vulkan-renderer/)
	- [[Vulkan Memory Management]]
	- [[Vulkan Barrier  Synchronization]]
- Parallel Computing
	- [[Vulkan Subgroups]]

#todo do this right

## Summary: Thread organisation
- Launching a kernel means running a list of _workgroups_
- Workgroups can be scheduled in any order
    
    - concurrent
    - no dependencies
    - each workgroup is started and freed as one (register file, shared memory)
- Subgroups in workgroup run concurrently
    
    - all threads in the workgroup are allocated and can run at the same time
    - subgroup runs in SIMD, if all threads in the subgroup take the same branch
- Subgroups are scheduled on the same SM (Streaming Microprocessor)
    
    - allows fast communication/barriers between subgroups in a workgroup via shared memory
    - within a single subgroup there is even faster communication (warp-level primitives/subgroup ops)
        - much like SSE/AVX instructions on CPU

## Summary: Memory organisation

- Address space separated into host and device memory
- Global device memory
    - potentially 150×
- - slower than registers
    - watch out for _coalesced_ reads and writes
    - accessible from device and also from host (limited)
    - lifetime of the application/persists between kernel launches
- Shared memory (per workgroup)
    - can be as fast as a register
    - lifetime of the workgroup
    - watch out for _bank conflicts_
- Registers (per thread)
    - fastest form of memory, only accessible by the thread
    - lifetime of a thread
    - allow fast interchange between threads in the same warp/subgroup

---

References: 
Tags: #📑
Created: 27.09.2024
