# Neural Backdoors
## Introduction

- subclass of model manipulation
- the goal is to manipulate the training of an AI model to shortcut the prediction to a predefined target/class
- <mark style="background: #FFB86CA6;">data poisoning</mark> 
	- mess with the training data
- <mark style="background: #FFB86CA6;">malicious training</mark>
	- mess with the training

## Data poisoning

- attack goal
	- indiscriminate poisoning -> reduce the overall accuracy of the model
	- targeted poisoning -> change a specific sample/class by introducing samples with a wrong label
- differentiation between dirty label and clean label attacks
- <mark style="background: #FFB86CA6;">poisoning rate</mark> - how many malicious samples have been introduced ($D_C$ are the clean samples. $D_P$ are the poison ones)
$$\rho = \frac{|D_P|}{|D_C| + |D_P|}$$

- e.g. when models are updated constantly online -> move the center of mass with constant malicious samples
	- in online learning, often the is a finite window used
	- ![[Pasted image 20260119121247.png | 300]]
- this can be generalized for [[Neural Networks]] by perturbating the inputs (clean label attack)
	- goal: classify the samples $X'$ as class $c$
	$$argmin_{\{\delta_x\}} \sum_{(x,y) \in D_C} L(f_\theta(x), y) + \sum_{(x,y) \in D_P} L(f_\theta(x + \delta_x, y) \ such\ that\ \sum_{x'\in X'} L(f_\theta(x'), c) \ is\ small$$
	- this is tricky because its a minimization task with two goals
		- do gradient alignment

- how realistic is that?
	- split-view data poisoning -> manipulate the data through different viewpoints on the data
		- e.g. data set is distributed as a list of urls -> buy expired urls and inject yout poisoned data
	- front-running poisoning -> manipulate the data that you know is used for the training
		- e.g. when snapshots of wikipedia are used

## Malicious Training

- manipulate the training itself, e.g. when you are the creator of the model itself
	- this allows for the manipulation of the loss function 
- used to create <mark style="background: #FFB86CA6;">Neural Backdoors</mark>, that shortcut to a predefined result $c$ through a specified trigger $T$
$$argmin_{\theta \in \Theta} \sum_{(x,y) \in D_C} (1 - \lambda) L_{benign}(f_\theta(x, y)) + \sum_{(x,y) \in D_P} \lambda L_{adv}(f_\theta(x \oplus T, y))$$
![[Pasted image 20260120175911.png]]

## Malicious Architecture

- same as malicious training but the trigger is embedded straight into the implementation of the forward pass through the model
- such a backdoor survives re-training

## Defenses

### Training Time Defenses

- Thread model: attacker controls the data, the defender the learning process
- Filter poisonous samples and implement a robust training method 
	- the combination of both would be <mark style="background: #FFB86CA6;">Anti-Backdoor Learning</mark> -> unlearn the malicious behavior $- \sum_{(x,y) \in D_P} \lambda L_{adv}(f_\theta(x, y))$
- how to find the poisonous samples? 
	- they are learned faster then benign samples -> but how to set the cutoff? That's an open research question
	- ![[Pasted image 20260120180722.png]]

### Runtime Defenses

- Thread model: attacker controls everything to deployment and distribution
- detect attacks as they happen (similar to [[Intrusion Detection]]) 
	- overlay input with a random other test sample
	- is the input has a trigger, the prediction is rather stable, if not then not
![[Pasted image 20260120181031.png]]

## Model Analysis and Repair

- analysis through statistics and [[Explainable AI (XAI)]]
- if detected, back-door removal through <mark style="background: #FFB86CA6;">fine-pruning</mark>
	- pruning - remove unneeded neurons
	- fine-tuning - refine model using clean data
---

Origin: 
References: 
Tags: 
Created: 19.01.2026

