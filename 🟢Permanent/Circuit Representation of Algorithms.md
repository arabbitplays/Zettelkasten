# Circuit Representation of Algorithms

- Represent computation as directed acyclic graph
	- ![[Pasted image 20241029100941.png |200]]
- Inner nodes compute a function in $O(1)$
- The indegree is bounded by a small constant -> no variable input data to the nodes
- The <mark style="background: #FFB86CA6;">depth</mark> is the longest path from input to output
	- this is the span (see [[Analysis of parallel Algorithms]])
- One circuit for every input size (specified algorithmically) is a <mark style="background: #FFB86CA6;">circuit family</mark>

---

Origin: Parallele Algorithmen
References: [[Parallel Machinemodels]]
Tags: 
Created: 29.10.2024

