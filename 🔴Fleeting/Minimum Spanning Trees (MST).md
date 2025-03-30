# Minimum Spanning Trees (MST)

## Problem Definition

- Undirected Graph $G = (V, E)$ 
	- $n = |V|$, $m = |E|$
- Edge weight  $c(e) \in \mathbb{R}_+$ 
- $G$ is connected, so every two nodes have a path between them

**Find a tree $(V, T)$ with minimum weight $\sum_{e \in T} c(e)$ that connects all nodes.**

- <mark style="background: #FFB86CA6;">The cut property</mark>
	- For any $S \subset V$ consider the cut edges $C = \{\{u, v\} \in E : u \in S, v \in V \backslash S\}$
	- **The lightest edge can be used in an MST**
- <mark style="background: #FFB86CA6;">The cycle property</mark>
	- **The heaviest edge on a cycle is not needed for an MST**

## The Jarník-Prim Algorithm

Idea: grow a tree with the help of the cut property

 - Start with $S = \{s\}$ for any node $s$ and $T = \emptyset$ 
 - do $n-1$ times: 

---

Origin: 
References: 
Tags: 
Created: 30.03.2025

