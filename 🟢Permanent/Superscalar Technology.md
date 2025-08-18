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

