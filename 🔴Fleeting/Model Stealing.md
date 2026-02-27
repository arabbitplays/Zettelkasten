# Model Stealing

## Introduction

- the goal is, to steal a model from a [[machine Learning as a Service (MLaaS)]] application
- learn a surrogate model with a query dataset $Z$ and its outputs from the application
- model approximation by either
	- getting the same results than the original model 
		- $max(E_{(x,y) \sim P_{xy}}[g(x) = y]$
	- getting similar results on a specific data distribution
		- $max(E_{x \sim P_x}[sim(f(x), g(x))])$
	- getting exactly the same functionality as the target model
		- $f(x) = g(x), x\in X$
	- getting exactly the same model
		- $f = g, \theta_f = \theta_g$ 
- attack strategies
	- analytic attacks
		- needs a lot of knowledge about the system
	- learning based attacks
		- query input output pairs and learn the surrogate model through that
		- needs to minimize the needed query count
## Attacker knowledge

- most often a gray box attack
- system knowledge
	- training algorithm, hyper-parameters, optimizer, ...
- task and domain knowledge
	- what task is solved by the system and implicitly the input domain
- output knowledge
	- often defined by the API interface
- model-view knowledge
	- alternative views on the model like the gradients from [[Explainable AI (XAI)]] methods
	- or sidechannel information from the model

## Data availability

- abundant data
	- access to dataset that is representative of the domain
- partial data
	- only o a subset of the training data is given
- no data
	- need to sythesise new data with a fitting generator

## Active learning

![[Pasted image 20260221103816.png]]
- pick the most informative samples to query

## Adverserial examples

- see also [[Adversarial Examples]]
- with whitebox adverserial examples, probe the descicion boundary through perturbations
	- learn from both the perturbated and original input
	- ideal a symmetric pairs, having the boundary in between them
- black bpx advererial examples try to solve the same problem, trying to find a similar surrogate model

- example: MAZE, a no data attack
![[Pasted image 20260221104819.png]]


## Knowledge destillation

- train a student model based on a teacher model -> very similar to model stealing

- example: DisGUIDE, a no data attack
	- to train the generator, the disagreement between the two surrogates is used instead of the surrogate vs the target model
![[Pasted image 20260221105008.png]]

## Defending against model stealing

- try to detect unusual behavior
	- attacks from multiple accounts still possible
- watermark your own model through [[Neural Backdoors]] 
---

Origin: ML and Security lecture
References: [[ML in IT security]]
Tags: 
Created: 21.02.2026

