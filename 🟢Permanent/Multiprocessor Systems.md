# Multiprocessor Systems

## introduction

- parallel systems can be categorized in 2 dimensions
	- distributed or common address spaces
	- global memory or physical distributed memory
	- global memory with common address space: [[uniform memory architecture (uma)]]
	- distributed memory with shared address space: [[distributed shared memory (dsm)]]
	- distributed memory with distributed address space: [[distributed memory multiprocessor]]
- to model runtime of algorithms, [[parallel machinemodels]] are used

## cluster

- for supercomputers, often the system is hyprid
	- every node of the system has shared memory, using [[OpenMP]] for programming
	- the nodes have distributed memory to each other, using [[Message Passing Interface (MPI)]] to communicate

## Accelerator

- in modern systems, accelerators like GPUs are used too (like [[CUDA Introduction | CUDE]])
- fitting parts of the program are shifted to the accelerators 

---

Origin: 
References: 
Tags: 
Created: 25.08.2025

