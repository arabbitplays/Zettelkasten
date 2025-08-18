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

### Branch Prediction

- static branch prediction - always assume the same direction for the prediction
- dynamic branch prediction - make a better prediction at runtime through the observed behavior of the program
	- way harder but way better predictions
- <mark style="background: #FFB86CA6;">Branch target address cache (BTAC)</mark> - store the program counter (PC) of a jump or branch instruction together with their target address
	- when fetching a jump instruction, check if the current PC is in the cache
		- if yes, use the stored target address as the new PC
		- if no, add it to the cache with the calculated target address
	- needs some time to fill up and only is beneficial if jumps are done multiple times
- <mark style="background: #FFB86CA6;">Branch prediction buffer (BPB)</mark> - store one bit showing if a branch was taken the last time
	- when fetching a branch instruction, check if the bit is set 
		- if yes (taken T), use the address in the BTAC
		- if no (not taken NT), proceed with the normal 
	- after evaluating the condition, update the BPB if needed
	- for better predictions, two bits can be used for strongly/weakly taken/not taken
- <mark style="background: #FFB86CA6;">Correlation predictions</mark>
	- use the behavior of this and previous jumps for the prediction
		- $m$-bit shift register <mark style="background: #FFB86CA6;">(branch history register)</mark> where every branch pushes a 0 or 1 depending on it if way taken or not
		- used to pick one of the $2^m$ Pattern History Tables
	- <mark style="background: #FFB86CA6;">Pattern History Table</mark> - stores $n$-bit predictors like the BPB 
		- is indexed by the lower bits of the instruction address

## Multicycle Operations

- for example for floating point operations, the execution phase can take multiple cycles
	- pipeline is stopped for coming instructions if a conflict is detected
![[Pasted image 20250811130120.png]]
---

Origin: 
References: 
Tags: 
Created: 02.08.2025

