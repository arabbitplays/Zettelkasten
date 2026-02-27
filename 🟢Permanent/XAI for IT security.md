# XAI for IT security

## Introduction

- evaluate learning based methods (e.g. [[Malware Classification]]) through understanding what the model does ([[Explainable AI (XAI)]])

- functional understanding
	- how do input and output relate to each other
	- determined with an explanation method $h_\theta(.)$ 
- model analysis
	- describe a models class ($h_\theta(X)$)
	- determine the input with the highest activation for a class, or a representative from the trainingsset that is close to the center
- decision analysis 
	- explain a single instance ($h_\theta(x_i)$)
	- find the parts of the input that are most relevant for the results (e.g. heat map for image inputs)
![[Pasted image 20260105110313.png]]

## Explaining a single instance

- this focuses on feature attribution -> highlighting relevance of features
	- find a relevance vector $r = (r_1, \dots, r_d)$ 
- for a linear model where $F_\theta(x) = sign(\langle x, w \rangle + b)$
	- direct map of weights to features so $r = w$
- for non-linear models, it is not that easy as there is not direct relationship between weights and features
	- consider relative changes, so what makes a dog less/more a dog and propagate this relevance
	- $$\frac{\partial f_\theta(x)_y}{\partial x_i}$$

## Layer-wise Relevance Propagation (LRP)

- in neural networks, we want the relevance of all $L$ layers
	- $$r_i^l = \sum_{j:node\ in\ layer\ l+1} \frac{a_i^l W_{ij}^l}{\sum_{k:node\ in\ layer\ l} a_k^l W_{kj}^l}r_j^{l+1}$$
	- the relevance of the layer $l+1$ is distributed to the nodes of layer $l$ based on the ration of contribution (ratio of the red line to all the green lines)
	- ![[Pasted image 20260105111900.png | 200]]
- this definition fulfills the relevance conservation
	- $\sum r_i^{(1)} = \sum r_i^{(2)} = \dots \approx f_\theta(x)$
- because all parameters need to be known for this, this is called <mark style="background: #FFB86CA6;">white-box explanation</mark>
	- <mark style="background: #FF5582A6;">such methods are specific for a given model (not general)</mark>
	- <mark style="background: #BBFABBA6;">but they provide the most accurate information</mark>

## Black-box Explanations

- no knowledge about the model or its parameters
	- <mark style="background: #BBFABBA6;">methods are agnostic to the model that is used</mark>
	- <mark style="background: #BBFABBA6;">internals of a model don't have to be known (for privacy or integrity reasons)</mark>
	- <mark style="background: #FF5582A6;">results are only approximate, gets worse the more not-linear and complex the model is</mark>
- approximate the decision boundary through surrogate models
	- either globally by learning the output of the entire classifier
	- or locally by breaking it down to localized regions (e.g. LIME)

### LIME

- LIME = Local Interpretable Model-Agnostic Explanations
- approximates regions of the decision boundary on nearby samples
	- perturbate the input and watch how the output changes
- ![[Pasted image 20260105112503.png | 300]]
- Choice of surrogate model is very important
	- data representation must be interpretable
	- is must be simple enough to be interpretable but complex enough to fit

## Evaluating Explanations

- generally important
	- descriptive accuracy 
		- how well are relevant features captured?
		- remove the $k$ most relevant features and predict again -> observe the decay
	- descriptive sparsity
		- indicating everything as important is not useful -> measure the sharpness of the normalized histogram
- especially important for security
	- completeness
		- explanations must be derived for all corner cases
			- an adversary may make use of pathological data
		- explanation must be a fundamental design property
	- stability
		- explanation must not vary over time
			- multiple runs must produce the same results 
	- efficiency
		- not a strict requirement but useful
		- does is delay the workflow?

---

Origin: 
References: [[Explainable AI (XAI)]], [[Malware Classification]]
Tags: 
Created: 05.01.2026

