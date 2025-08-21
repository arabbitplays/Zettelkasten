# Software Development Processes

## Introduction

- A software process model is an abstract representation of a software development process
	- which activities should be carried out and by who
	- which products should be developed until when
- for example the waterfall model, V-model, ...
- this is the basic sequential Waterfall Model
![[Pasted image 20250821110834.png]]
- pro for processes
	- roles support specialisation
	- phases help structure a project
	- big tasks can and must be divide and conqered
- cons against processes
	- roles can lower productivity as not everyone is needed at the same time
	- planning and realization need to stay close together as the world is chaotic

## The Waterfall and what is wrong with it

- giant projects can take multiple years of development, and may be in use or maintained for decades
	- requirements can change drastic
	- such time frames can not be planned ahead
- there are no feedback cycles for replanning or redesign
	- changes invalidate the whole planning, design or implementation

## Iterative Processes

- to mitigate these problem, processes become iterative
	- feedback from the last cycle can be incorporated
	- the requirements get refined and can be changed if needed
- <mark style="background: #FFB86CA6;">iterative</mark> models jump back to the design phase of the Waterfall
	- projects grows in increments
- <mark style="background: #FFB86CA6;">evolutionary</mark> models jump back to the planning phase
	- this means the whole Waterfall is run through multiple times

## Unified Process (UP)

- in the end it comes down to find a way to incorporate development phases, testing and risk management in an iterative way => UP
	- UP is the process counterpart to [[Unified Modelling Language (UML)]]
- the UP defines 
	- 4 phases to be concluded with a milestone (NOT the Waterfall phases)
	- 9 disciplines, 6 technical and 3 supporting
		- they are all part of all iterations, but different disciplines are most important at different times
		- each of them run through their own Waterfalls 
![[Pasted image 20250821112529.png]]
- <mark style="background: #FFB86CA6;">Inception</mark>
	- "Envision the project scope, vision and business case"
	- is it feasible? what is the unreliable cost range? should the project be proceeded?
- <mark style="background: #FFB86CA6;">Elaboration</mark>
	- build core architecture
	- resolve highly risky elements
	- define most of the requirements
	- estimate overall schedule and resources
- <mark style="background: #FFB86CA6;">Construction</mark>
	- build the rest in increments while refining the requirements
	- prepare for deployment
- <mark style="background: #FFB86CA6;">Transition</mark>
	- Beta tests and deployment

- the <mark style="background: #FFB86CA6;">Rational Unified Process</mark> is a concrete implementation of the UP
	- approach for assigning tasks and responsibilities through roles in an organization 
	- very heavyweight and must be tailored to real needs in practice
- alternatives are a more lightweight implementation of UP like [[Agile Development]]

---

Origin: 
References: [[Agile Development]]
Tags: 
Created: 21.08.2025

