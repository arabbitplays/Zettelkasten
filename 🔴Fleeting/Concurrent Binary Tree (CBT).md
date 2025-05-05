# Concurrent Binary Tree (CBT)

## Introduction

## Construction
- the whole thing is a 1D array of unsigned integer
- split in two parts
	- The back part is a bit field representation of a binary tree
	- the first part is a perfect binary tree used to iterate over the leafs of the represented binary tree

- binary tree representation (second part)
	- the binary tree can be unperfect
	- a bit field where each 1 is a leaf in the binary tree
	- the number of zeros behind the 1 gives the depth of the leaf

- Index names:
	- leaf Index indexes into an Imaginaty array of all the leaf Nodes
	- heap Index is an Index into the binary tree represented by the second part  
	- bit Index is the Index of the bit in the second part that encodes a given heap Node
		- one bit Index can encode multiple heap Nodes, but it is clean which is meant through the number of 0 bits that follow 

---

Origin: 
References: 
Tags: 
Created: 30.04.2025

