# Software Architecture

## Introduction

- A software architecture is 
	- the result of a set of design decisions
	- comprising the <mark style="background: #D2B3FFA6;">structure of the system given the requirements</mark>
		- with components
		- their relationships 
		- their mapping to execution environments
- questions to be answered by the decisions
	- how will the system be decomposed into subsystems
		- which are reusable?
	- what management and evolution strategy should be used
		- [[Model Driven Architecture]]
- [[Model Views]] can be used to describe and document architectural decisions
## Architecture Patterns and Styles

- <mark style="background: #FFB86CA6;">Architectural pattern</mark> - solution to recurring problem on an architectural level ([[Model-View-Controller (MVC)]], Client-Server, Blackboard, ...)
- <mark style="background: #FFB86CA6;">Architectural style</mark> - solution principles, used throughout the whole architecture (like object-oriented, or modular)

- Architecture is influenced by the requirements, both functional and non-functional, the amount of possible or planned reuse and the team structure
	- decoupled parts can be parallelized but will also mirror the styles of the different teams

### Layered Architecture

- Modern OO systems are usually grouped in layers each consisting of one or more subsystems having a cohesive responsibility
	- higher levels call lower levels
	- improves modifiablility and brings clearer separation of concerns
- Layers:
	- UI, Presentation
	- Application
		- handles UI requests, session state, ...
	- Domain
		- implementation of domain rules and services
	- Business Infrastructure
		- general low-level business services
	- Technical Services
		- persistence, security, ...
	- Foundation
		- utilities, frameworks, ...
		- data structures, DB, network I/O, ...
- domain model is not the same as domain layer
	- model is only the important objects in the requirements
	- layer adds more classes needed for a full implementation
		- for example <mark style="background: #FFB86CA6;">Data Transfer Objects (DTO)</mark>

---

Origin: 
References: 
Tags: 
Created: 08.05.2025

