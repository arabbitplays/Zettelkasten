# Use Cases

## Introduction

- use cases define an interaction between two parties
	- most often between a user and a black box system
- for a use case the system boundary, actors and goals must be defined
- can come in text or diagram form ([[Unified Modelling Language (UML)]])
![[Pasted image 20250823112549.png | 500]]
## Picking the right granularity

- the common levels are summary use case, user goal (EBP), sub use case and system operation
- good rule of thumb: focus on <mark style="background: #FFB86CA6;">Elementary Business Process (EBP)</mark>
	- a task performed by one person at one place at one time
	- in response to a business event, which adds measurable business value
	- and leaves data in a consistent state
- some more heuristics
	- imagine your boss asks you what you have been doing all day? how pleased would he be if you answer...
		- "I have been logging in" -> to small use case
		- "I have been creating customer accounts" -> better
	- would you take a coffee break after finishing the use case?
		- would you leave after searching a list of customers you need to edit
		- or rather after you edited and saved the data

## Fully Dressed Use Case

1. Preface elements
	- scope, goal level, primary actor, ...
2. Stakeholder and Interest list
	- source for each responsibility
3. Pre conditions
	- what is assumed before the use case is started
4. Post conditions
	- what needs to be true after the use case is done
5. Main success scenario
	- the typical path where everything works out and every stakeholder is satisfied
6. Extensions
	- Alternative branches of both success and fail
	- every extension point should have a condition and a handling part
	- if the extension point is too complex, make a new use case for it
7. Special requirements
	- non-functional requirements and constraints specific for the use case
8. Technology and data variations
	- technical variations in how things must be done
	- different possible data schemes

---

Origin: 
References: [[Model Driven Software Development (MDSD)]], [[Requirement Engineering]], [[Unified Modelling Language (UML)]]
Tags: 
Created: 23.08.2025

