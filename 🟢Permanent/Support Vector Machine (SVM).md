# Support Vector Machine (SVM)

## Introduction

- modern supervised learning algorithm for [[Klassifikation | classification]] 
- a hyperplane separating the data with maximum margin 
	- [[Regularisierung | regularisation]] through softening the boundary
	- supports [[Kernels in ML | kernels]] for learning and training

## Learning Model

- learn a weight vector $w$ and a bias $b$
- decision function
$$f(z) = sign(\langle \phi(x), w\rangle + b)$$
![[Pasted image 20251213141806.png]]
- maximize margin $M$ -> same as minimizing $||w||$
- with labels $y_i \in \{-1, 1\}$ this has to be always true:
$$y_i (\langle \phi(x_i), w \rangle + b) \geq 1\ for\ all\ i$$

- regularisation through slack variables $\xi_i$ 
	- small $C$ is a smooth boundary, large C is a firm decision boundary
	- the $\xi_i$ are learned and are constrained to $\xi_i \geq 0$
$$min_{w, b, \xi}\ ||w||+C \sum \xi_i$$
$$with \ y_i (\langle \phi(x_i), w \rangle + b) \geq 1 - \xi_i\ for\ all\ i$$

![[Pasted image 20251213142142.png]]

## One-class support vector machines

- finds the minimum hypersphere enclosing the data
- made robust against outliers through regularisation
$$min_{\mu, R}\ R^2$$ $$with \ ||\phi(x_i)-\mu|| ^2 \leq R^2\ for\ all\ i$$
- regularisation through slack variables $\xi_i$ 
	- small $C$ is a smooth boundary, large C is a firm decision boundary
	- the $\xi_i$ are learned and are constrained to $\xi_i \geq 0$
$$min_{\mu, R, \xi}\ R^2+C \sum \xi_i$$
$$with \ ||\phi(x_i)-\mu|| ^2 \leq R^2+\xi_i\ for\ all\ i$$
![[Pasted image 20251117123150.png | 300]]


---

Origin: 
References: 
Tags: 
Created: 13.12.2025

