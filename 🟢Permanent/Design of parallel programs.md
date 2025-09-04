# Design of parallel programs

## Introduction

- basic problem of determining which parts of the program should (or can) be parallelized
- the solution to this can be manual, semi-automatic (tool supported) or automatized (parallelizing compiler)
- generally, memory access should happen locally, as access time is significantly higher on distant then on local access
- central factor is the <mark style="background: #FFB86CA6;">calculation/communication ratio</mark>

## Design Phases by Foster

1. Partitioning phase
	- The calculation steps and the data on which they get executed get split into smaller parts
	- not dependent on specific system parameters
	- main goal is to produce as much theoretical parallelization as possible
2. Communication phase
	- determine the necessary communication  requirements for the coordination of work
	- find or develop data structures and communication algorithms these requirements
3. Aggregation phase
	- bundle up different calculation steps and communication structures if necessary
	- this could be due to performance increases through less communication overhead or saved cost in design and implementation
4. Mapping phase
	- map work and data to specific processors for maximum utilization and minimal communication cost
	- can be done static or dynamic through [[Load Balancing]]

### Partitioning Phase

- <mark style="background: #FFB86CA6;">Domain decomposition</mark>
	- split data in parts where a good load balance and minimal communication can be expected
	- can be static  (done by the compiler or programmer) or dynamic (done at runtime) as well
	- generally, focus either on the biggest data structure or the one with the most access
- <mark style="background: #FFB86CA6;">Functional Decomposition</mark>
	- focus on splitting the tasks in groups that can run in parallel
	- assign the needed data to the task (ideally this can be done disjunctive)
		- if data needs to be shared, communication is needed
		- if a lot of communication is needed, domain decomposition might be better

### Communication Phase

- determine which tasks depend on the resulting data of other tasks
- abstract view on communication through modeling it as channels, that simply connect two tasks
- for functional decomposition the data flow is often pretty clear, less so for domain decomposition
- local vs global communication 
	- local communication means each tasks only communicates with neighbors (like for convolutions)
	- global communication is more general (like Master/Worker Schemes)
- structured vs unstructured communication 
	- structured communication means that channels create a structured pattern, like a tree, ring or chain
	- unstructured communication creates a general graph
- static vs dynamic communication 
	- in static communication, communicating partners stay the same
	- in dynamic communication, partners depend on calculation results
- synchronous vs asynchronous communication patten
	- producing and consuming partners either work in sync or the need for communication happens irregular

### Aggregation Phase

- three conflicting goals:
	- reducing communication costs through coarser granularity
	- keeping flexibility for mapping phase and scaling
	- reducing cost for software engineering
- <mark style="background: #FFB86CA6;">surface-to-volume effect</mark> - communication cost is proportional to the surface of the subdomain, while computation cost is proportional to the volume
	- imagine a cube that is split into sub cubes, then the sub-cubes only need to communicate with their neighbors on its borders
- communication can be reduced through calculating tasks multiple times

### Mapping Phase

- map tasks to processors, so that the final execution time in minimized
	- give independent tasks to different ones
	- while tasks with a lot of communication should be mapped to the same or at least neighboring ones
- see [[Load Balancing]] 

## Programming for Multiprocessor Systems

- for [[Distributed Memory Multiprocessor]] systems that communicate through messages, us [[Parallel Communication Patterns]] to achieve efficient communication
- for shared memory systems, the [[Cache Coherence Problem]] is central
	- to still get efficient code, use [[Variable Analysis]]

---

Origin: 
References: [[Parallel Computing Index]], [[Variable Analysis]]
Tags: 
Created: 04.09.2025

