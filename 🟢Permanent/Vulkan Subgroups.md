# Vulkan Subgroups

- Tasks are split on multiple GPU PEs where they run concurrently
	- All tasks on one PE are calles the <mark style="background: #FFB86CA6;">local workgroup</mark>
	- Each task individualy is calles an <mark style="background: #FFB86CA6;">invokation</mark>
	- One PE can run multiple invokations in parallel


- The workgroup is all the invokations that should run on this PE
- The subgroup is all the invokations on the PE that run in parallel


## GL_KHR_shader_subgroup_basic

- `gl_NumSubgroups` is the number of subgroups within the local workgroup.
- `gl_SubgroupID` is the ID of the subgroup within the local workgroup, an integer in the range $[0..gl\_NumSubgroups)$

- `bool subgroupElect()` - exactly one invocation within the subgroup will return true, the others will return false. The invocation that returns true is always the one that is active with the lowest `gl_SubgroupInvocationID`.
## GL_KHR_shader_subgroup_arithmetic

---

Origin: https://www.khronos.org/blog/vulkan-subgroup-tutorial
References: 
Tags: 
Created: 27.11.2024

