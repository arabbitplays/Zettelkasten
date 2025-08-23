# Uniform Memory Architecture (UMA)

## Introduction

- alternate name: <mark style="background: #FFB86CA6;">symmetric multi-processor systems (SMP)</mark>
- parallel computing systems that share a common memory 
	- global address space
- communication and synchronization is done over variables
- very popular both in servers and desktop systems (see every multi-core processor)
![[Pasted image 20250812113434.png | 400]]


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

