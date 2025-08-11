# Reliability of Computer Systems

## Introduction

- <mark style="background: #FFB86CA6;">dependability</mark> - ability of the system, to fulfill a specific function in the right conditions for a given amount of time
- <mark style="background: #FFB86CA6;">safety</mark> - a state that has no danger for humans and objects, so that no segnificant damage can happen

## Dependability

- <mark style="background: #FFB86CA6;">fault</mark> - reason for an error, some defect in a component
- <mark style="background: #FFB86CA6;">error</mark> - non-intended state of a component, are created through faults
- <mark style="background: #FFB86CA6;">failure</mark> - a component in an error state uses its ability to function

- faults can be classified by the life cycle of the system
	- during the design phase (specification fault, implementation fault, documentation fault)
	- during the production
	- during the usage 
		- influences from outside like elctric or magnetic fields
		- wear and thear of the components
- faults can be classified by their duration
	- permanent faults
	- sporadic/intermitted  faults
		- unregular and short term faults, that can produce permanent faults
	- transient faults
		- unregular and short term faults, that don't produce permanent faults
- failure classification
	- components can lose some of their functionality, all of it, give no result or sometimes (but then correctly), or give the correct result but with some wrong binaries
- system behavior under failure
	- fail-stop system - the system gives no result under failure
	- fail-silent system - the system gives no results for some time
	- fail-safe system - a system that has no critical failures

### Fault-tolerance

- the ability of a system to have no failures even when there are faults in some components
- <mark style="background: #FFB86CA6;">propability of survival</mark> - chance that a mission succeeds
- <mark style="background: #FFB86CA6;">mean survival time</mark>
- <mark style="background: #FFB86CA6;">reliability</mark> - time a interactive server can be used

- redundancy - components can be replaced on the fly
	- dynamic redundancy - redundant components get activated after a failure of another component happened (replacement)
	- static redundancy - redundant components just exist side by side
- structure function models - results of faults can be pinned to a certain region of the system without spreading
	- directed graph, a node is a components, the is an edge if a component relies on the functionality of the other component
	- can be structured in layers

- fault probability - $F_L(t) = \frac{N_f(t)}{N}$
	- chance that the system is in an error state after time $t$
	- $N_f(t)$ is the number of components that are in an error state after time $t$
- reliability - $R(t) = \frac{N_s(t)}{N}$ 
	- chance that a system stays error free util time $t$
	- $N_s(t) = 1 - N_f(t)$
- failure rate - $z(t) = \frac{d}{dt}F_L(t) \frac{1}{R(t)}$
	- the relative number of failing components in regard to the non faulty components
- Mean lifetime - $E(L) = \int_0^\infty R(t)dt$
## Safety

![[Pasted image 20250801103228.png]]

---

Origin: 
References: 
Tags: 
Created: 01.08.2025


