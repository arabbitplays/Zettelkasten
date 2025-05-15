# Parallel Machinemodels

## Modelling problems from real computers

- Asychronous - design, analysis and debugging is more complicated
- Contention for memory modules, cells or the network
- Memory hierarchy with different speeds
- Networks between processors do not scale linear

## [[Uniform Memory Architecture (UMA)]]

## Work Span Model

- Use work and span to abstract away from PE count $p$ (see [[Analysis of parallel Algorithms]])
$$T(p) = \frac{W}{p} + T_\infty$$
- Use fork to create new tasks and use work stealing [[Load Balancing ]] to achieve the expected time above

## [[Distributed Memory Multiprocessor]]

## Bulk Synchronous Parallel (BSP)

- Cycles are supersteps consisting of 3 steps
	- Local computations in every PE for $w$ cycles
	- Constant global coordination time $L$
	- Global collective message exchange with time $g$ per word and the longest message having $h$ words
- Superstep takes $w + L + gh$ time
- <mark style="background: #FF5582A6;">It is not clear how this gets combined with network costs</mark>
	- with naive direct delivery of all messages: $L \geq \alpha\ log\ p$ and $g \geq \alpha$

### BSP*

- Alternative view: not machine words are sent but blocks of messages of size $B$ -> $h$ counts these blocks, not words
- It is easier to implement this model on real machines with the point-to-point network costs

### BSP+

- add collective operations to the BSP model (broadcast, reduce, ...) 
	- see [[Message Passing Interface (MPI)]]
	- is by a factor of $\Theta(log\ p)$ faster then BSP*

## MapReduce

![[Pasted image 20241029092252.png |400]]
- $\mu$ and $\rho$ are programable
- the shuffle step puts every key value pair into sets with the same key
- Very abstract -> no load balancing, memory hierachies, ...
- produces large overheads and limited functionality

---

Origin: Parallele Algorithmen
References: [[Analysis of parallel Algorithms]]
Tags: 
Created: 24.10.2024

