# Memory Consistency Models

## Introduction

- they define in which order memory operation become visible to other processors in a [[Uniform Memory Architecture (UMA) | Multiprocessor System]]
- in contrast, the [[Cache Coherence Problem]] only cares about the behavior of multiple operations on the same memory address
- for the two operations read (R) and write (W), consistency models are defined in terms of rules in the form of $X \rightarrow Y$
	- means that $X$ has to be completely finished before $Y$ starts
- weakened consistency is fine as long as programs ensure correct ordering of memory operations through [[Synchronization]]

## Sequential Consistency

- $R \rightarrow R,\ R \rightarrow W,\ W \rightarrow R,\ W \rightarrow W$
- means the system handles memory access strictly sequential like one processor would do it
	- write access has to be [[Atomare Operationen | atomic]]
- a memory access is only then finished, when all cache invalidation signals are finished
- <mark style="background: #FF5582A6;">loss of performance</mark>

## Release Consistency

- all orders are released
- programmers have to define critical sections in which the consistency is broken
	- avoid competing access through proper synchronization

---

Origin: 
References: [[Cache Coherence Problem]]
Tags: 
Created: 13.08.2025

