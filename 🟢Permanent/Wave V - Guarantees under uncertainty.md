# Wave V - Guarantees under uncertainty

## Introduction

- definition of uncertainty in the SAS context

- uncertainty is a state that involves imperfect and/or unknown information
	- through physical measurements
	- underspecification of the problem or solution space
	- numerical approximations
	- non-determinism
- is applies to prediction of future events

- key insights
	- Uncertainty in self-adaptive systems is defined as any <mark style="background: #D2B3FFA6;">deviations</mark> in deterministic knowledge that may <mark style="background: #D2B3FFA6;">reduce the confidence</mark> in adaptation decisions made based on this knowledge
	- Uncertainty can appear in the<mark style="background: #D2B3FFA6;"> system itself</mark>, its <mark style="background: #D2B3FFA6;">goals</mark>, the <mark style="background: #D2B3FFA6;">context</mark> in which it operates, and through <mark style="background: #D2B3FFA6;">humans</mark> involved in the system
	- Taming uncertainty refers to <mark style="background: #D2B3FFA6;">providing guarantees for compliance</mark> of the system with its adaptation goals, despite the uncertainties the system is exposed to
	- Taming uncertainty requires an <mark style="background: #D2B3FFA6;">integrated engineering process</mark> that spans implementation, enactment, runtime adaptation, and evolution.
## Classification

- <mark style="background: #FFB86CA6;">aleatory uncertainty</mark> 
	- inherent uncertainty due to randomness of a phenomenon
	- for example in measurements
	- is irreducible
- <mark style="background: #FFB86CA6;">epistemic uncertainty</mark>
	- a lack of knowledge about the system
	- for example ambiguous or imprecise information about the requirements or the environment of the system
	- is reducible, as more information can help
- Location of the uncertainty
	- context uncertainty identifies the boundaries of the model
	- structure uncertainty is concerned with the form of the model itself
	- input parameter uncertainty is in regard to the input data given to the model
![[Pasted image 20251213133916.png]]
![[Pasted image 20251213134244.png]]

- mitigation of uncertainty
	- ... in input parameters:
		- confidence intervals, probability distributions, fuzzy methods,
		- range of values, mean and variance, and sensitivity analysis
	- ... in context and models:
		- model averaging
		- model discrepancy.

## Taming uncertainty in SAS using formal analysis techniques

- this is a two step decision making process using [[Wave III - Runtime Models | models at runtime]]
	- Analyzer and verifier analyse adaptation options
	- planer selects best adaptation option
![[Pasted image 20260409135305.png | 500]]
![[Pasted image 20260409135407.png | 500]]


---

Origin: [[Self-adaptive Systems.pdf]]
References: [[Self-adaptive Systems]]
Tags: 
Created: 04.12.2025

