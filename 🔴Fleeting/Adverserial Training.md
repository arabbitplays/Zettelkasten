# Adverserial Training

## Introduction

- counter measure against [[Adversarial Examples]]
- find best attacks $\delta$ and minimize their empirical risk
$$min_\theta \frac{1}{n} \sum_i^n max_{\delta_i} L(x_i + \delta_i, \theta, y_i)$$
- in training, use FGSM or PGD adverserial examples
	- can overfit very badly
	- can be a bit better when attacks $\delta$ are chosen randomly in the beginning
	- early stoppage

- other challenges
	- tradeof between adverserial robustness and normal accuracy
	- expensive computation
	- hoe well the robustness generalizes

## Robust Error

- example for a 2-class classifier
- the <mark style="background: #FFB86CA6;">natural error</mark> is the normal accuracy of the model
- the <mark style="background: #FFB86CA6;">boundary classification error</mark> is defined over correctly classified samples in the boundary region $B$
- ![[Pasted image 20260123110402.png | 300]]
- <mark style="background: #FFB86CA6;">robust error</mark> is then the sum of both
---

Origin: 
References: 
Tags: 
Created: 23.01.2026

