# Pipelining

## Introduction

- here in the sense of achieving parallelism in processors through pipelining all steps to execute an instruction
	- for pipelining in parallel algorithms see [[Parallel Computing Index]]
- given $n$ instructions and $k$ pipeline stages
	- sequential execution: $n * k$
	- pipelined execution: $n + k - 1$

## Instruction Pipelining

- the five basic pipeline steps are instruction fetch, instruction decode, execute, memory access and write back
- <mark style="background: #FFB86CA6;">pipeline conflicts</mark> are moments when a pipeline stage from a specific instruciton can not be executed at a given time
	- resource conflicts - parallel write access on a register with just one entry
	- data conflicts - a instruction needs the result of an instruction that hasn't been executed (or something similar)
	- control conflicts - through jump instructions it is not clear which next instruction to put in the pipeline
- resolving conflicts:
	- add an empty step to delay the next instruction
	- reordering the instruction through the compiler
	- predicting the control flow to minimize chances of having to clear the pipeline

## Multicycle Operations

- for example for floating point operations, the execution phase can take multiple cycles
	- pipeline is stopped for coming instructions if a conflict is detected
![[Pasted image 20250811130120.png]]
---

Origin: 
References: 
Tags: 
Created: 02.08.2025

