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
- $pos = \sum_{i < j} l_i$
- Sequential:
	- for every job, assign the part of the job to PE $j$
	- if PE $j$ has no more free space, continue with $j + 1$ and assign the rest of the job to it
- Parallel:
	- every job $j$ can calculate its PEs with $\lfloor pos / C \rfloor \dots \lfloor (pos + l_j) / C \rfloor$
	- $C + O(\frac{n}{p} + log(p))$ if jobs are distributed randomly
![[Pasted image 20250401100321.png | 300]]

- if the jobs are atomic
	- assign job to $\lfloor pos / C \rfloor$ -> 2-approximation
	- better approximation if large jobs get assigned first, but propably not parallelizable

## Unkown Sizes

- best distribution though random permutation with an all-to-all communication
	- problem is getting a parallel generation of a random permutation
- $L = \sum l_i$
- $l_{max} = max\ l_i$
- If $L \geq 2(\beta +1)pl_{max}\frac{ln(p)}{\epsilon^2} + O(1 / \epsilon^3)$
	- then whp the max load is $(1+ \epsilon)\frac{L}{p}$
	- which is fine if $l_{max}$ is not that big
- <mark style="background: #BBFABBA6;">its irrelevant where jobs come from and how big they are</mark>

### Random Permutation

- interpret numbers from $0 .. n-1$ as tupel from $\{0 .. \sqrt n - 1\}^2$
- get a (pseudo) random function $f : 0..\sqrt n - 1 \rightarrow 0..\sqrt n- 1$
- chain <mark style="background: #FFB86CA6;">Feistel Permutation</mark> $\pi_f((a,b)) = (b, a + f(b)\ mod\ \sqrt n)$ 
$$\pi(x) = \pi_f(\pi_g(\dots(x)\dots))$$

### Master-Worker Scheme

- all jobs are on master-PE
- job sizes can be estimated 

---

Origin: Parallel Algorithms Lecture
References: [[Parallel Computing Index]]
Tags: 
Created: 26.03.2025

