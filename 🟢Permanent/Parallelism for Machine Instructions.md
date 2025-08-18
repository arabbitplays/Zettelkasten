# Parallelism for Machine Instructions

## Introduction

- CPUs use different techniques to execute machine code more efficiently in parallel
- concurrency - execute multiple instructions truly parallel
	- dynamic approach: [[Superscalar Technology]]
	- static approach: [[Very Long Instruction Word]]
- [[Pipelining]] - overlap the execution of multiple instructions

## Multithreading

- for RISC and Superscalar CPUs there still are downtimes
	- Multicyclic instructions, pipeline conflicts, cache misses, ...
- fill these times by switch to another runable thread
	- switch has to be really fast
- a thread in this context is just a control flow with its own instuction pointer
	- threads share their address space so they can interact
- <mark style="background: #FFB86CA6;">Cycle-by-Cycle Interleaving</mark>
	- for every cycle, the processor chooses one of the runable threads (Round Robin)
	- if a thread results in waiting cycles, it is skipped
	- <mark style="background: #BBFABBA6;">no true data dependencies</mark>
	- <mark style="background: #FF5582A6;">individual runtime of a thread is greatly increased</mark>
- <mark style="background: #FFB86CA6;">Block Interleaving</mark> 
	- run one thread until it results in waiting time, then switch the thread
	- <mark style="background: #BBFABBA6;">threads run the same time</mark>
	- <mark style="background: #FF5582A6;">pipeline has to be cleared -> only for long wait times</mark>
- <mark style="background: #FFB86CA6;">Hyperthreading</mark> - combine multithreading with [[Superscalar Technology]]

---

Origin: 
References: [[Parallel Computing Index]]
Tags: 
Created: 11.08.2025

