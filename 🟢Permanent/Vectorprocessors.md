# Vectorprocessors

## Introduction

- processors that have a special unit for vector arithmetic
- SIMD according to [[Flynn's Taxonomy]]

## Vector Pipelines

- split on operation on an entry of the vector into multiple steps
	- send all entries of the vektor through this pipeline
- <mark style="background: #FFB86CA6;">multifunctional pipeline</mark> - one pipeline that can do all vektor operations though many pipeline steps
	- skip the steps that are currently not needed
- <mark style="background: #FFB86CA6;">specialized pipelines</mark> - one pipeline for each connection of vectors

## Memory Interleaving

- memory is structured in $n$ memory banks with own address logic
- allows parallel memory access
- address $i$ is saved in memory bank $j$ when $j = i\ mod\ n$ 
	- vectors are distributed over the banks and can be loaded parallely

## Strides

- for matrices, columns (or sometimes rows) are not next to each other in memory
- but in the vector registers the vector has to be compact
- solution: special stride register with the number of bytes between entries
	- loading operations read the stride register and load the vector entries accordingly
	- for example, write the row length in the stride register to load a column compactly in a register

## Vector Masks

- problematic code:
	- operation is not done on every entry of the vector
```C
for (int i = 0; i < 64; i++) {
	if (X[i] != 0) {
		X[i] = X[i] + Y[i];
	}
}
```
- solution:
	- precalculate a boolean vector with the condition
	- load it in the vector masking register
	- calculate $X = X+Y$ -> processor skips the masked entries

---

Origin: 
References: [[Parallel Machinemodels]]
Tags: 
Created: 13.08.2025

