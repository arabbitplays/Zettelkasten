# Requirement Engineering

## Introduction

- Definition <mark style="background: #FFB86CA6;">requirement</mark> 
	- a condition or capability needed by the user to solve a problem or achieve an objective
	- a condition or capability that needs to be met to satisfy a contract, specification or other document
	- there are functional requirements, quality requirements and constraints
- requirement engineering is a cooperative and iterative process of
	- <mark style="background: #FFB86CA6;">Requirement Elicitation</mark> - seeking and capturing requirements from available sources
	- <mark style="background: #FFB86CA6;">Requirement Decumentation</mark> - persist the elicited requirements and create a specification
	- <mark style="background: #FFB86CA6;">Requirement Agreement</mark> - resolve conflicts and find requirements that are acceptable for all (or most) stakeholders
		- Different stakeholders have different viewpoints or political interests

![[Pasted image 20250822125307.png]]
- the context is the part of the domain that is relevant to understand the system and its requirements
- the requirements formulated in the world must be translated into requirements for the system/machine
	- world requirement: For every turnstile, the system shall count the number of persons passing through this turnstile.
	- machine requirement
	- Machine Requirement: The turnstile control software shall count the number of ‘unlock for a single turn’ commands it issues to the controlled turnstile.
	- Only holds for the assumption, that when the turnstile is unlocked, only one person passes through

## Elicitation

- techniques for elicitation
	- ask  - interview stakeholders or use questionaires
	- observe - observe stakeholders in their work context
	- analyze - work artifacts, problem reports, market studies or benchmarks
	- collaborate - hold a requirements workshop
	- build & play - experiment with prototypes and mockups, perform role playing
- eliciting constraints
	- technical, e.g.  through interfaces to other systems
	- legal
	- organizational
	- environmental, cultural, ...
- requirement kind
	-  functional requirements, quality requirements and constraints
- requirement representation
	- Operational - specification of operations or data, tested through review, test or formally
	- Quantitative - Specification of measurable properties, tested through measurements
	- Qualitative - Specification of goals, testes through subjective judgement
	- Declarative - Description of a required feature, tested through a review
- requirement satisfaction - when is it fulfilled (soft vs hard)

 - The modern approach: User-Stories ([[Agile Development]]) or [[Use Cases]] ([[Model Driven Software Development (MDSD)]])
	- both focus on interaction of users and the system

## Validation

- very important and requirement error become harder to fix the longer they are there
![[Pasted image 20250822132555.png|400]]

- review - author guides experts through the specification -> feedback cycle
- acceptance test cases - force the specification to become concrete
- simulation / animation - for dynamic system behavior
- prototyping
- formal verification / [[[Models]] Checking

## Traceability

- means that a requirement can be connected to its origin, design, implementation, tests and dependent requirements
![[Pasted image 20250822132727.png]]
- can mean a lot of manual work or needs good systems like in [[Model Driven Software Development (MDSD) | MDSD]] to be possible automatically

---

Origin: 
References: [[Use Cases]]
Tags: 
Created: 22.08.2025

