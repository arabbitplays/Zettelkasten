---
date created: 31.01.2024 14:39
date modified: 13.08.2024 15:13
---

# Design by Contract

## Introduction

- Contracts make it possible to verify the correctness of software formally
- for example implemented by [[Java Modelling Language (JML) | JML]]

## Notes

- Correctness of software is relative to the specification
	- Specification can also be incorrect
- <mark style="background: #FFB86CA6;">Validation</mark> is the testing of the software with the most important equivalence classes of the input
- <mark style="background: #FFB86CA6;">Verification</mark> is the all-quantified proof that software is correct for the entire input

- Specification between contract between supplier and client of a service
	- Who does what?
	- Under what conditions?
- Based on <mark style="background: #FFB86CA6;">Hoare Triples</mark> $\{P\}\ C\ \{Q\}$ 
	- If precondition $P$ applies, postcondition $Q$ applies after $C$ has been executed
	- Client must fulfill $P$ and can assume $Q$
		- All components of $P$ must be accessible to the client <mark style="background: #FFB86CA6;">(Post Condition Availability)</mark> 
	- Supplier must fulfill $Q$ and can start from $P$
- <mark style="background: #FFB86CA6;">Non-Redundancy Principle</mark>
	- If preconditions are specified, the supplier should NOT test them <mark style="background: #FFB86CA6;">(Demanding)</mark>
	- Only if none are given can the supplier perform checks themselves <mark style="background: #FFB86CA6;">(Tolerant)</mark>
- Eiffel is a programming language with built-in contracts

---

Origin: Programmierparadigmen Vorlesung
References: [[Java Modelling Language (JML)]]
Tags: 
Created: 25.04.2025

