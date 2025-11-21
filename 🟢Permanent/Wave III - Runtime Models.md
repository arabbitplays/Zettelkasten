# Wave III - Runtime Models

## Introduction

- happened from about 2009 to 2014
- the concrete realization of self-adaptation is complex
- the model-driven approach is extended to runtime to have different runtime models supporting decision-making

- a <mark style="background: #FFB86CA6;">runtime model</mark> is a first-class runtime abstraction of a system, used for self-adaptation
- they can be incomplete and are updated based on observations of the system and its environment
- a <mark style="background: #FFB86CA6;">"weak" causal connection</mark> allows a discrepancy between the state of the model and the system that does not invalidate the adaptation goal

## Dimensions of Runtime Models

- structural vs. behavioral
	- like in [[Unified Modelling Language (UML)]]
- declarative vs. procedural
	- what needs to be done and how it is done
	- the goal vs the plan to reach the goal
- functional vs. qualitative
	- the model represents either the functionality of a system or qualitative aspects
	- when it represents the functions <mark style="background: #FFB86CA6;">(functional model)</mark>, it can be used to check if an adaptation still fulfills the functions
	- when it represents the qualitative aspects <mark style="background: #FFB86CA6;">(runtime quality model)</mark> like response time, memory usage, ... adaptation options can be ranked based on these aspects
		- for example Markov chain models, determining the chance to land in a fail state or queue models, determining wait times and queue lengths of queue systems
- formal vs. informal
	- informal are user stories, semi-formal like [[Unified Modelling Language (UML) | UML]] or [[SysML]] or formal like Finite-State Machines, Markov Models, ...

---

Origin: 
References: 
Tags: 
Created: 20.11.2025

