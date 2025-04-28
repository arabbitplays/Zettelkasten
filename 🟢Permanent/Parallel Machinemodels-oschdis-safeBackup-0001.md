# Parallel Machinemodels

## Modelling problems from real computers

- Asychronous - design, analysis and debugging is more complicated
- Contention for memory modules, cells or the network
- Memory hierarchy with different speeds
- Networks between processors do not scale linear

## Parallel random access machine - PRAM 

- like the von Neumann Modell (RAM) where cycles are counted and memory is freely programmable
- using $p$ <mark style="background: #FFB86CA6;">Processing Elements (PE)</mark> like multiple processors that are <mark style="background: #D2B3FFA6;">fully synchronized</mark>
- shared global memory
	- multiple versions depending is the read (R) and write (W) is concurrent (C) or exclusive (E) -> EREW, CREW, CRCW
	- multiple versions of CRCW PRAM depending on how conflicts are resolved
		- <mark style="background: #FFB86CA6;">common</mark> - all PEs have to agree
		- <mark style="background: #FFB86CA6;">arbitrary</mark> - some PE succeeds (not random, but it has to be not important who)
		- <mark style="background: #FFB86CA6;">priority</mark> - smallest ID succeeds
		- <mark style="background: #FFB86CA6;">combine</mark> - values are combined by some operator

## Asynchronous PRAM

- aCRQW: write is queued (Q) meaning it takes $O(k)$ if $k$ PEs write concurently
- its important that the algorithm is correct, regardless how long an operation need
- use [[Atomare Operationen#Compare and Swap| Atomic Operations]] to have consistent writes

## Work Span Model

- Use work and span to abstract away from PE count $p$ (see [[Analysis of parallel Algorithms]])
$$T(p) = \frac{W}{p} + T_\infty$$
- Use fork to create new tasks and use work stealing [[Load Balancing ]] to achieve the expected time above
## Parallel External Memory (PEM)

- Models memory hierarchy
- Each PE is its own RAM
	- has its own local memory $M$ 
	- is naturally asynchronous
- There is additionally a shared global memory that can be accessed in blocks of size $B$
	- For the shared memory, all the PRAM variations exist

### Network Costs

- Modelling the whole network structure is complicated ([[Netztopologie]])
	- in practice, bandwidth and interconnections are plenty enough to assume constant costs for every communication partner -> <mark style="background: #FFB86CA6;">Fully connected point-to-point</mark>
- $T_{Comm}(m) = \alpha + m \beta$ for message length $m$
- Destinction between 
	- <mark style="background: #FFB86CA6;">half-duplex</mark> - send OR recieve from another PE
	- <mark style="background: #FFB86CA6;">telephone</mark> - send and recieve from PE $j$
	- <mark style="background: #FFB86CA6;">duplex</mark> - send and recieve from any PE

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

