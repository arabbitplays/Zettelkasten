# Branch-and-Bound

## Definition

- $H = (V, E)$ - tree with bounded node degree
- $c(v)$ - costs of a node, growing when descending a path
- $v^*$ - leaf with minimal cost
- $\widetilde{V} = \{v \in V | c(v) < c(v^*)\}$ - all nodes that are discovered before $v^*$ 
- $m = |\widetilde{V}|$
- $h$ - depth of $\widetilde{H}$, the subgraph of $H$ induced by $\widetilde{V}$ 

- $T_x$ - time for generating a successor of a node
- $T_{coll}$ - upper bound for collective operations for one element (broadcast, prefix-sum, ...)
	- On most networks $\alpha\ log\ p$


#TODO sequential and parallel algorithms
---

Origin: 
References: 
Tags: 
Created: 29.03.2025

