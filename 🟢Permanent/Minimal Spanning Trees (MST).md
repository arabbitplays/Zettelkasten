# Minimal Spanning Trees (MST)

## Problem Definition

- Undirected Graph $G = (V, E)$ 
	- $n = |V|$, $m = |E|$
- Edge weight  $c(e) \in \mathbb{R}_+$ 
- $G$ is connected, so every two nodes have a path between them

**Find a tree $(V, T)$ with minimum weight $\sum_{e \in T} c(e)$ that connects all nodes.**

- <mark style="background: #FFB86CA6;">The cut property</mark>
	- For any $S \subset V$ consider the cut edges $C = \{(u, v) \in E : u \in S, v \in V \backslash S\}$
	- **The lightest edge can be used in an MST**
- <mark style="background: #FFB86CA6;">The cycle property</mark>
	- **The heaviest edge on a cycle is not needed for an MST**
- <mark style="background: #FFB86CA6;">Edge contraction</mark>
	- given an MST edge $(u,v)$, eliminate $v$
	- for every edge $(w,v) \in E$
		- $E = E \backslash (w, v) \cup (w, u)$
	- remember the original terminals
	- ![[Pasted image 20250330151913.png | 300]]

## The Jarník-Prim Algorithm

Idea: grow a tree with the help of the cut property

 - Start with $S = \{s\}$ for any node $s$ and $T = \emptyset$ 
 - do $n-1$ times: 
	 - find $(u,v)$ fulfilling the cut property with $S$
	 - add $v$ to $S$ and $(u,v)$ to $T$

- implement with an [[Graph Representations#Adjacency Array | Adjacency Array]] and a priority queue with the edge weight as a key
	- time outside of the PQ: $O(m+n)$
	- $n$ times delete min on the PQ: $O(n\ log(n))$
	- $O(m)$ times decrease key on the PQ: amortized $O(m)$
	- using Fibonacci Heaps: $O(m + n\ log(n))$ 
- <mark style="background: #FF5582A6;">inherently sequential</mark>
	- only PQ can be parallelized

## Kruskal's Algorithm

- Idea: connect more and more subtrees of $G$ (builds on the cycle property)

- Start with $T = \emptyset$
- iterate through $E$ in ascending order of weight
	- if $(u,v)$ connects two different subtrees in $T$, add the edge to $T$

- implement with an Union-Find data structure
	- $O(sort(m) + m\alpha(m, n)) = O(m\ log(m))$
		- $\alpha$ is the inverse Ackermann function
- <mark style="background: #FF5582A6;">inherently sequential</mark>
	- only sorting can be parallelized

## Boruvka's Algorithm

 - for each node, find the lightest incident edge
	 - add to the MST (cut property)
- contract these edges with edge contraction

- implement with an [[Graph Representations#Adjacency Array | Adjacency Array]] 
	- sequentially its $O(m\ log(m))$

### Parallel Implementation

- a second *predecessor graph* will be constructed

1. Find lightest incident edge
	- every node gets PEs proportional to the number of incident edges ($|\Gamma(v)|\frac{p}{2m}$) 
	- find $min_w c(v,w) \in \Gamma(v)$ (this is a reduction)
	- output $v, w$
	- *set $pred(v) = w$*
		- this results in pseudo-trees (trees with one additional edge) with one two-cycle at the lightest edge
		- ![[Pasted image 20250330153353.png | 200]]
	- $O(\frac{m}{p} + log\ p)$
2. Convert Pseudotrees to Rooted Trees 
	- parallel for every node $v$
		- if $v < pred(v) \wedge v = pred(pred(v))$ then $pred(v) = v$
	- ![[Pasted image 20250330153704.png | 200]]
	- $O(\frac{n}{p})$ 
3. Convert Rooted Trees to Rooted Stars
	- while $v \in V$ exists with $pred(pred(v)) \neq pred(v)$ do parallel for all $v$ // runs max $log(n)$ times
		- pointer doubleling: $pred(v) = pred(pred(v))$
	- ![[Pasted image 20250330155005.png | 200]]
	- $O(\frac{n}{p}log\ n)$
4. Contraction
	- Assign the star roots new node numbers (with a bijective function $f$ through a prefix sum)
	- construct a new edge set $E' = \{(f(pred(u)), f(pred(v))): (u,v) \in E, pred(v) \neq pred(u)\}$
	- ![[Pasted image 20250330155422.png | 100]]
	- $O(\frac{m}{p}+ log\ p)$
5. Convert $G'$ into an adjacency array (integer sorting)
	- expected sorting time on CRCW PRAM ([[Parallel Machinemodels]]) in $O(\frac{m}{p}+ log(p))$ when the keys are in $O(m\ log^k(m)$
	- optional: remove parallel edges, but they are hard to find
		- sorting after $u$ and $v$, but then the keys are in $O(n^2)$
6. Recursion on $G'$ 

- Total time: $O(\frac{m}{p}log(n) + log^2(n))$
	- Max $log(n)$ recursions, because in every level, at least $n/2$ MST edges are found
	- Problem is the conversion to rooted stars because $log(n)*O(\frac{n}{p}log(n))$ is too slow
		- but the $n$ is getting smaller in every level
		- $\sum \frac{n}{2^i}log(\frac{n}{2^i}) \leq \sum \frac{n}{2^i}log(n) = n\ log(n) \sum 2^{-i} = O(n\ log(n))$ 

## Filter Kruskal

1. if $m$ is small enough, use normal Kruskal
2. While sorting, partition edges into $E_\leq$ and $E_>$ (like quicksort)
3. Recursion on $E_\leq$_ result is $T$ 
	- If $T$ already has $n-1$ edges, return
4. Filter $E_>$: if an edge closes a circle in $T$, remove the edge
5. Recursion on $E_>$

### Parallel Implementation

- Partitioning/sorting can be done in parallel
- Filtering can be done in parallel (removeIf operation)

---

Origin: 
References: [[Graph Representations]]
Tags: 
Created: 30.03.2025

