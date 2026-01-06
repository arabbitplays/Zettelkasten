# Adversarial Examples

## Introduction

- an attack against a ML model
- manipulate the input into the model in a way, that misleads the prediction function
- possible usecase is to develop [[Malware]] that is not detected by  [[Malware Classification]]
![[Pasted image 20260106122147.png | 200]]
$$arg\ min_\delta\ ||\delta||_p\ such\ that\ F_\theta(x+\delta) = c \neq y$$
- just try arbitrary changes <mark style="background: #FFB86CA6;">(sparse attack)</mark> or constraint changes <mark style="background: #FFB86CA6;">(dense attack)</mark> to try to find the decision boundary
![[Pasted image 20260106122334.png]]
- either <mark style="background: #FFB86CA6;">targeted</mark>, minimizing the loss with a target class $L(f_\theta(x+\delta), c)$ or <mark style="background: #FFB86CA6;">untargeted</mark>, maximizing the loss with the true class $L(f_\theta(x+\delta), y)$ 

## Inverse Feature Mapping Problem

- sometimes input is transformed to be representable in vector space
- then ther eis no easy way from features to actual sample
![[Pasted image 20260106123440.png]]
## Constraints on Adversarial Example

- use different norms to constrain $\delta$
- limit attack to a specific location $||M \bigodot \delta||_p$
- problem space constraints
	- adverserial app must still be functional
	- qualitativr properties must be preserved for a realistic attack
	- is it robust against pre-processing (e.g. removing unreachable code)

## Generating Adversarial Examples

- perturbation has the constraint $||\delta||_p \leq \epsilon$
- for linear models, the shortest path crossing the boundary is the direction of the weight vector $w$ -> $\delta = \epsilon \frac{w}{||w||}$
- ![[Pasted image 20260106123838.png | 300]]

### Fast Gradient Signed Method (FGSM)

$$\langle x + \delta, w \rangle + b = \langle x, w \rangle + \langle \delta, w \rangle + b$$
- this is maximized if $\delta = \epsilon\ sign(w)$ which fits the constraint under the max norm
- this argument holds for non-linear models
$$\delta = \epsilon\ sign(\Delta_x L(f_\theta(x), y))$$

### Projected Gradient Descent (PGD)

- one step of FGSM is not always enough in non-linear models
![[Pasted image 20260106124657.png]]
- so the goal is like [[Gradient Descent]] but in reverse, starting at a random position and going up the gradient of the loss function
- here [[Regularisierung]] can also be used

## Defense against Adversarial Examples

- no strong defense known today
	- many approaches are broken by white-box attacks or an adaptive attacker
	- white-box here means direct access to the prediction function
	- adaptive means an attacker can adapt to the system and the defense
	- input data is inherently in the control of the attacker

- <mark style="background: #FFB86CA6;">integrated defense</mark> - attack-resilient learning algorithms
- <mark style="background: #FFB86CA6;">operational defense</mark> - security-aware application of learning

- defense: obfuscate prediction function by choosing more complex predictor or using noise added to the output
	- both is broken by approximating the predictor with a surrogate model 
- defense: stateful application, monitor access and detect unusual behavior
	- only feasible with remote access to the model
	- using multiple accounts still breaks it
- defense: security-aware testing
	- testing for corner cases, around the boundary, ...
	- training of multiple models
	- [[XAI for IT security]]
	- still does not remove the inherent problems

---

Origin: 
References: 
Tags: 
Created: 06.01.2026

