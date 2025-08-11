# Superscalar Technology

## Introduction

- a processor has multiple independent execution units, allowing to execute multiple instruction truly parallel in one clock cycle
	- this is a parallelisation of the execution phase of normal [[Pipelining | Pipelines]]
- detection and resolution of conflicts between instruction is done by the hardware dynamic at runtime
![[Pasted image 20250811131350.png]]

- the execution units don't have to be identical, they can be specialized for integer or floating point operations, memory access or media control

## Superscalar Pipeline

- new pipeline phase called Dispatch/Issue, where instructions a assigned dynamically to different execution units
- instruction fetch, decode and dispatch are in-order, while the execution is out of order, meaning the instructions are not executed in the order of the program
	- after the execution, the write back phase is in-order again to make the results valid in the right order
- instruction fetch gets multiple instructions -> high chance for control conflicts
	- <mark style="background: #FFB86CA6;">branch prediction</mark> - make assumptions over the jump condition and fill waiting cycles with the predicted instructions
		- if prediction was correct, proceed normally
		- if not, throw away the instructions (rollback of the pipeline)
- all pipeline stages have instruction buffers between each other

### Branch Prediction

- static branch prediction - always assume the dame direction for the prediction
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

###  Register Mapping

- in the instruction decode phase: map target register in the instruction to unused physical registers
	- avoids some data conflicts (write after read and write after write)
- differentiate architecture registers (seen by the instructions) and shadow registers, used to buffer the results

### Dispatch/Issue Phase 

- instructions are assigned to different execution units
- resolves true data dependencies and resource conflicts through a scheduler
	- checks which instruction are ready to run
- <mark style="background: #FFB86CA6;">Reorder buffer</mark> - order of the instructions are added here to restore the order after the out-of-order execution phase

#### Tomasulo Procedure

- when an instruction is dispatched, an entry is added to the reservation station of the execution unit
- <mark style="background: #FFB86CA6;">Reservation station</mark> - table for every unit storing the destination register, the source registers, which unit calculates the source values and flags if the source registers are already valid
	- this allows for multiple units to be served with the source values at the same time
- when all source registers are valid, the instruction is issued 

### Retire Phase

- according to the reorder buffer, the results are made valid through copying them from the shadow registers to the architecture registers
	- only make it valid if all previous instructions have finished and if the instruction is not dependent on speculation

---

Origin: 
References: [[Parallelism for Machine Instructions]], [[Pipelining]]
Tags: 
Created: 11.08.2025

