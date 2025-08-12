# OpenMP

## Introduction

OpenMP is a standardized programming interface (API) that was developed for portable
programming of [[Uniform Memory Architecture (UMA) | parallel computers with shared memory]] (or
shared address space)

- basic execution model
	1. A thread enters a parallel region, creates a thread team an becomes their master thread
	2. The thread team splits the work, does it an is implicitly synchronized through a barrier
	3. Only the master thread keeps on working after the parallel region

## OpenMP Directives

```c++
#pragma omp directive [clause[clause]...]
```
- there are directives for parallelization, synchronization and data usage
- each directive has clauses to specify more 
	- `private` and `shared` specify which variables should be shared and which should be local for the threads
	- `if` gives a condition for when the block should be parallelized

## Runtime Routines

- there are routines in the library `omp.h` that set parameters of the runtime environment
	- `omp_set_num_threads()` sets the number of threads in a thread team
	- `omp_get_num_threads()` gets the number of threads in a thread team
	- `omp_get_wtime()` gets the time since a fixed point in the past

## Work sharing constructs

- Data parallelism
	- `#pragma omp parallel for` - iterations of the following loop get distributed over the threads
- Task parallelism
	- each thread gets one section
```c++
#pragma omp sections [clause(s)]
{
#pragma omp section
	<code block 1>
#pragma omp section
	<code block 2>
}
```

## Synchronization

- `#pragma omp barrier` - all threads of the team have to reach this barrier to keep on working
- `#pragma omp atomic` - memory access in the following instruction has to be atomic
- `#pragma omp critical [(<name>)]` - all critical sections with the same name share one lock
---

Origin: 
References: [[Parallel Computing Index]]
Tags: 
Created: 12.08.2025

