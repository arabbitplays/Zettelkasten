# Distributed Shared Memory (DSM)

## Introduction

- [[Parallel Computer Systems]] that have distributed memory but share a common address space
	- its common, that memory access to address in the local memory module is faster than to the local memory of another processor <mark style="background: #FFB86CA6;">(Non-uniform memory access (NUMA))</mark>
- often caches are used
	- when [[Cache Coherence Problem | Cache Coherence]] is maintained across all processors, its a <mark style="background: #FFB86CA6;">CC-NUMA</mark> system
	- or caches or only used for local memory access, its a <mark style="background: #FFB86CA6;">NCC-NUMA</mark> system
- three types of DSM
	- memory access is transparent for machine instruction (often on CC-NUMA)
	- instruction set is extended for distant memory (often on NCC-NUMA)
	- Software DSM

## Software DSM

- illusion of a shared memory is achieved through software o computer clusters
	- [[Synchronization]] is important
- page-based approach
	- use [[Paging]] of the OS
	- coherence protocols are valid per-page
- object-based approach
	- DSM is realized through explicitly stated memory region

## False sharing and flattering

- different data on the same page is needed by two processors at the same time
	- because coherence has to be secured, the page has to be taken from one processor before another can write
	- processors are blocked often as pages has to be sent over the networks
- flattering is the effect that pages are sent often
- how to mitigate the effect
	- smaller pages minimize the chance, that two needed works are on the same page
---

Origin: 
References: [[Distributed Memory Multiprocessor]], [[Uniform Memory Architecture (UMA)]]
Tags: 
Created: 25.08.2025

