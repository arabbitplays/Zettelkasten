# Wave IV  - Requirements

## Introduction

- from 2009 to 2015 the main research focus was on requirements-driven self-adaptation 

- <mark style="background: #FFB86CA6;">goal-modeling</mark>
	- means to decompose technical and non-technical requirements into well-defined entities (goals)

## Goal-oriented requirements engineering

- <mark style="background: #FFB86CA6;">Contextual Goal Model (CGM)</mark> 
	- composed of actors, goals, tasks, and context
	- actors: humans or software that can make decicions
	- goals: abstractions of stakeholder needs
	- tasks: operational steps to fulfill goals
	- context: part of the environment that can influence goals and means of achieving them
- Refining goals and tasks
	- into an AND-decomposition where each subgoal or subtask must be fulfilled
	- inta an OR-decomposition where one subgoal or subtask must be fulfilled

## Uncertainties in the requirements

- see als [[Wave V - Guarantees under uncertainty]]
- to mitigate uncertainties in the fulfillment of requirements
	- a subtask can be added to mitigate uncertainty -> for example filtering read data
	- or requirements can be realaxed
		- Model operators - SHALL, MAY or ...)
		- Temporal operators - fulfill goal AS SOON AS POSSIBLE or only IN INTERVAL
		- Ordinal operators - AS CLOSE TO X AS POSSIBLE, AS MANY AS POSSIBLE
- optimal fulfillment of requirements can be integrated into the SAS like that

---

Origin: [[Self-adaptive Systems.pdf]]
References: [[Self-adaptive Systems]]
Tags: 
Created: 09.04.2026

