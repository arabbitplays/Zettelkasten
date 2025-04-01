# Load Balancing

- How to assign jobs to multiple processors while minimizing
	- maximum load on any PE
	- time for finding and executing the assignment
- Jobs can have known, approximate or unknown size 
- Jobs can be subdivisible or not
- PEs can have (fluctuating) external load, if for example they are part of a public cluster

## Simple Model

- $n$ jobs that are independend, splittable and have a description of size $O(1)$
- Size $l_i$ is exactly known

### Next fit

- work per PE is $C = \sum l_i / p$
- Sequential:
	- for every job, assign the part of the job to PE $j$
	- if PE $j$ has no more free space, continue with $j + 1$ and assign the rest of the job to it
- Parallel:
	- every job $j$ can calculate its PE with $\lfloor \sum_{i < j} l_i \rfloor$
![[Pasted image 20250401100321.png | 300]]

---

Origin: Parallel Algorithms Lecture
References: [[Parallel Computing Index]]
Tags: 
Created: 26.03.2025

