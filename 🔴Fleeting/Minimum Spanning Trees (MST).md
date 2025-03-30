# Minimum Spanning Trees (MST)

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

- a second 

1. Find lightest incident edge
	- every node gets PEs proportional to the number of incident edges ($|\Gamma(v)|\frac{p}{2m}$) 
	- find $min_w c(v,w) \in \Gamma(v)$ 
	- 

---

Origin: 
References: 
Tags: 
Created: 30.03.2025

