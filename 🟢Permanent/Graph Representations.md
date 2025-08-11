# Graph Representations

## Adjacency Matrix

- if the is an edge between node $i$ and node $j$, set $A[i][j]$ to $1$
- if the graph is undirected, the matrix is symmetric
- <mark style="background: #FF5582A6;">not very memory efficient</mark>

## Adjacency Array

- Store graph as two arrays $V$ and $E$
- $V$ stores an index of $E$ for every node
- $E$ stores all the adjacent nodes for a given node, starting at the index stored in $V$ as well as the weight $c$ of the edge
![[Pasted image 20250330150614.png]]

- <mark style="background: #BBFABBA6;">given a node, gives fast access to the incident nodes</mark>
- for more flexibilty: use linked lists for the parts of $E$ <mark style="background: #FFB86CA6;">(Adjacency list)</mark> 
---

Origin: 
References: 
Tags: 
Created: 30.03.2025

