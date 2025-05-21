# Uniform Memory Architecture (UMA)

## Introduction

- alternate name: <mark style="background: #FFB86CA6;">symmetric multi-processor systems (SMP)</mark>
- parallel computing systems that share a common memory 
	- global address space
- communication and synchronization is done over variables
- very popular both in servers and desktop systems (see every multi-core processor)

## Parallel random access machine - PRAM 

- like the von Neumann Modell (RAM) where cycles are counted and memory is freely programmable
- using $p$ <mark style="background: #FFB86CA6;">Processing Elements (PE)</mark> like multiple processors that are <mark style="background: #D2B3FFA6;">fully synchronized</mark>
- every processor has the same latency on the main memory (symmetric access)
- programming is relatively easy
- as soon as caches are between the main memory and each processor, the <mark style="background: #FFB86CA6;">cache-coherence problem</mark> has to be solved
- shared global memory
	- multiple versions depending is the read (R) and write (W) is concurrent (C) or exclusive (E)
		- => EREW, CREW, CRCW
	- multiple versions of CRCW PRAM depending on how conflicts are resolved
		- <mark style="background: #FFB86CA6;">common</mark> - all PEs have to agree
		- <mark style="background: #FFB86CA6;">arbitrary</mark> - some PE succeeds (not random, but it has to be not important who)
		- <mark style="background: #FFB86CA6;">priority</mark> - smallest ID succeeds
		- <mark style="background: #FFB86CA6;">combine</mark> - values are combined by some operator

### Asynchronous PRAM

- aCRQW: write is queued (Q) meaning it takes $O(k)$ if $k$ PEs write concurently
- its important that the algorithm is correct, regardless how long an operation need
- use [[Atomare Operationen#Compare and Swap| Atomic Operations]] to have consistent writes
## Cache Coherence Problem

- Problem: PE A reads x into its cache, PE B writes to x => PE A has an outdated x in the cache
- a cache memory is called <mark style="background: #FFB86CA6;">(cache) coherent</mark> if a read on a value always results in the last written value
- a system is <mark style="background: #FFB86CA6;">consistent</mark>, if all copies of a memory word are identical over all caches => implies coherency
- consistency is not practical, as it requires a performance overhead, which makes having caches obsolete

---

Origin: 
References: 
Tags: 
Created: 14.05.2025

