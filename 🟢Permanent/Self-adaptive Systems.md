# Self-adaptive Systems

## Introduction

- self-adaptive systems are software systems that react to the environment with no or nearly no manual intervention
- ![[Pasted image 20251106095816.png | 400]]
- <mark style="background: #FFB86CA6;">environment</mark> - how many users, hardware, other application on the same hardware, ...
- <mark style="background: #FFB86CA6;">managed systems</mark> - the main system, having the domain concepts
- <mark style="background: #FFB86CA6;">managing systems</mark> - the control system, getting high level goals and adapting the managed system to these goals through a feedback loop
- there are many different types of feedback loops 
	- [[MAPE-K]]

## Waves of research

- the research in self adaptive systems can be structured into 7 waves
	- the 1. and 2. focuses on the fundamental principles of such systems
		- [[Wave I - Automating Tasks]], [[Wave II - Architecture-based Adaptation]]
	- the 3. and 4. focus on concrete aspects of the concrete realization of such systems
		- [[Wave III - Runtime Models]], [[Wave IV  - Requirements]]
	- the 5. and 6. focus on uncertainties as a key driver for self-adaptation
		- [[Wave V - Guarantees under uncertainty]]
	- the 7. focuses on exploiting [[Machine Learning Index | ML]] to support different functions of the system
		- [[Wave VII - Learning from Experience]]
		- especially [[Explainable AI (XAI)]] is crucial here

## Self-adaptation in the industry

- Self-adaptation is widely applied in industry across a wide variety of domains
	- optimise performance, automate tasks, and deal with changes in the deployment environment (changing loads, failures of services, ...)
	- improving user satisfaction (response-time, up-time, ...) and reducing costs, and secondarily mitigating risks
- elastic cloud and auto-scalers are key enablers for the realisation of self-adaptation in practice
	- for example Kubernetes or AWS
- Resource usage and system load are the main types of monitoring metrics used in practice
- Ensuring trust is mainly achieved through extensive testing, runtime monitoring and alerting, and human supervision.
	

---

Origin: [[Self-adaptive Systems.pdf]]
References: 
Tags: 
Created: 06.11.2025

