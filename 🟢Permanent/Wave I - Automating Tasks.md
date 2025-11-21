# Wave I - Automating Tasks

## Introduction

- focuses on the automating management tasks like self-optimization, self-healing, self-protection or self-configuration
- introduces the <mark style="background: #FFB86CA6;">MAPE-K</mark> loop and different forms of it

## Essential maintenance tasks

- <mark style="background: #FFB86CA6;">self-optimization</mark> is the capability to optimize resource, while providing the quality assignment
- <mark style="background: #FFB86CA6;">self-healing</mark> is the capability to detect and recover from faults
- <mark style="background: #FFB86CA6;">self-protection</mark> - protect against attacks and anticipate requirements
- <mark style="background: #FFB86CA6;">self-configuration</mark> - capability to automatically integrate new elements

## MAPE-K

![[Pasted image 20251106101520.png]]

- the <mark style="background: #FFB86CA6;">monitor</mark> collects the data, optionally pre-processes it and updates the relevant models of the knowledge
	- finally checks if analysis is required
- <mark style="background: #FFB86CA6;">analysis</mark> searches the best adaptation in the <mark style="background: #FFB86CA6;">adaptation space</mark>
	- different approaches to adaptation space reduction and exploration (heuristics, exhaustive search, machine learning, ...)
	- needs a mechanism to determine the quality of each option .> simulation, table-based, ...
		- knowledge over time can be used reactive, active (only the present) or proactive (predicted knowledge)
	- may need a strategy for a fail-safe state
- <mark style="background: #FFB86CA6;">plan</mark>
	- two examples for ranking mechanism
		- ranking based on expected utility
		- goals as threshold goals, so only the compliant options are ranked
- even multiple MAPE-K loops are possible, interacting in different patterns (example here would be a master-slave setup)
	- ![[Pasted image 20251106101825.png]]

### Knowledge

- four types of models are managed by the knowledge of a managing system
- <mark style="background: #FFB86CA6;">Managed System Model</mark>
	- self-awareness
	- represents the current configuration and data about quality properties
- <mark style="background: #FFB86CA6;">Environment Model</mark>
	- context-awareness
	- knowledge about uncertainties
	- represents the elements or properties of the environment in which the managed system operates
- <mark style="background: #FFB86CA6;">Adaptation Goals Model</mark>
	- goal-awareness
	- representation of the objectives
		- rule-based constraints, fuzzy goals, value constraints, utility functions, ...
- <mark style="background: #FFB86CA6;">Working Models</mark>
	- representation of the knowledge shared among MAPE components
		- domain specific models
## Automatic decision making

- for different properties (failure-rate, service cost, ...) define a utility preference function $p_i$ by the stakeholders and a property weight $w_i$ how important the property is
![[Pasted image 20251106102419.png | 500]]
$$U_c = \sum_i w_ip_i$$
- calculate for multiple configurations and pick the one with the highest utility
- self-configuration is possibile if new elements have a specific signal to transmit their existence
	- system responses with information on how the new element canintegrate into the system


---

Origin: 
References: 
Tags: 
Created: 06.11.2025

