# Evaluation of Computer Systems

## Introduction

- for the development and [[Design of computer systems]] it is important to evaluate the system
	- different approaches whether the system is already under use

## Benchmarks

- MIPS and MFLOPS - millions of (floating point) instructions per second
	- often just a best case metric given by the producer
	- depends heavily of the instruction set of the system
- often <mark style="background: #FFB86CA6;">benchmarks</mark> are used to get comparable data
	- collection of computation intensive programs 
		- LINPACK is used for the TOP 500 list and consists of solving linear equation systems
	- often no [[System Calls]] or communication needed -> no comparison to real applications
	- SPEC (Standard Performance Evaluation Corp.) - creates diverse benchmark suits for different applications
$$SPECratio_x = \frac{ReferenceTime_x}{Runtime_x}$$
- For all benchmarks in the suite, get the geometric average:
$$\sqrt[n]{\prod_i^n SPECratio_i}$$
- for comparing throughput (again with geometric average afterwards), run $m$ instances of the benchmark at the same time:
$$SPECrate = m_x * SPECratio$$

## Monitors

- Recording Elements that monitor the traffic on a running system
- <mark style="background: #FFB86CA6;">Hardware-Monitor</mark> - physical independent device that doesn't interfere with the runtime
- <mark style="background: #FFB86CA6;">Software-Monitor</mark> - integrated into the OS, does interfere with the runtime

### Hardware-Monitors

- count intern events in the CPU and in caches
	- executed instructions, runtimes in cycles, cache hits and misses, read and written bytes, ...
- there are producer specific routines to read these counters in c++
- Performance Application Programming Interface (PAPI)
	- producer independent API to read performance counters
	- allows derivation of user specific metrics depending on hardware specific metrics

## Model-Theoretical Approaches

- tries to model the relationship between relevant performance metrics and fundamental system parameters

### Example: Queue models

- $\lambda$: mean arrival rate (how many jobs arrive per unit time)
- $t$: mean time a job is in the wait system (mean response time)
- $w$: mean time a job is in the waiting queue (mean wait time)
- Laws of Little: 
$$L = \lambda * t, Q = \lambda * w$$
- $L$ is the mean number of jobs in the system, $Q$ is the mean number of jobs in the queue
## Simulation

- cost efficient and flexible way to test new ideas
- compromise between simulation speed, precision and design effort
- builds understanding for why measured behavior is the way it is

## Taxonomy

**Types of simulators:**
- <mark style="background: #FFB86CA6;">User-level simulators</mark>
	- simulates micro architecture of a processor
	- no regard to system resources, running on top of the OS
- <mark style="background: #FFB86CA6;">Full-system simulators</mark>
	- models a full computer system, including CPU, I/O,  disks and networwing
	- runs in the Host OS and simulates a target OS
- <mark style="background: #FFB86CA6;">Functional simulators</mark>
	- models only the functionality of microprocessors, without simulating how they really work
	- emulation of the instruction set architecture
- <mark style="background: #FFB86CA6;">Cycle-accurate simulators</mark>
	- captures every aspect of microarchitectures
	- emulates even the behavior regarding time
	- but allows architecture to parametrisised
		- caches, cache line length, size, ...
**How instructions to simulate are aquired:**
- <mark style="background: #FFB86CA6;">Trace-driven simulation</mark>
	- benchmark is run on a processor with the same instruction set as the simulator
	- the executed instruction are stored in a trace file 
		- trace file is used a the input for the cycle-accurate simulator
- <mark style="background: #FFB86CA6;">Execution-driven simulation</mark>
	- the executable of the benchmark is the input for the simulator
	- simulator must reproduce the functionality perfectly, which is hard to develop

---

Origin: 
References: [[Design of computer systems]], [[Reliability of Computer Systems]]
Tags: 
Created: 29.07.2025

