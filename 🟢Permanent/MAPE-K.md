# MAPE-K

## Introduction

- classic self-adaptive feedback loop, creating a managing system
- Monitor, Analyse, Plan, Execute + Knowledge
	- especially the Knowledge consists of different [[Wave III - Runtime Models | Runtime Models]]
- tries to satisfy Quality of Service (QoS) indicators for the managed system
![[Pasted image 20260412145853.png | 500]]
## Knowledge

- underlying knowledge base used by the other components
- describes the managed system and the current state of it
	- service implementations and their operational profiles
	- service configuration for load balancing etc
	- running service instances and their metric snapshots (QoS indicators like responsetime, CPU usage, ...)

## Monitor

- calls the <mark style="background: #FFB86CA6;">Probing API</mark> of the microservices and stores their snapshots in the knowledge
- triggers the next analyze loop

## Analyze

- estimates QoS indicators given the snapshots
- when quality requirements are violated, adaptation proposals are provided and stored in the knowledge

## Plan

- adaptation proposals for each service are evaluated to estimate their benefit (utility value)
- selects the best ones by solving an optimization problem
	- mixed integer linear programming
- the chosen option for each service is stored in the knowledge

## Execute

- processes the adaptation plan by calling the <mark style="background: #FFB86CA6;">Actuator API</mark> of the microservices
- notifies the Monitor that the loop ended

---

Origin: [[Self-adaptive Systems.pdf]]
References: 
Tags: 
Created: 09.04.2026

