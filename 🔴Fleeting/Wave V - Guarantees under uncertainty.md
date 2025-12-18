# Wave V - Guarantees under uncertainty

## Introduction

- definition of uncertainty in the SAS context
- details on quantitative verification

- uncertainty is a state that involves imperfect and/or unknown information
	- through physical measurements
	- underspecification of the problem or solution space
	- numerical approximations
	- non-determinism
- is applies to prediction of future events

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

---

Origin: 
References: 
Tags: 
Created: 04.12.2025

