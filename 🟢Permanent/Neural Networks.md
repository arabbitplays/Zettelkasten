# Neural Networks

## Introduction

- very powerful machine learning model that can be adapted into all sorts of more advanced models
	- [[Rekurrente Neuronale Netze (RNN)]]
	- [[Convolutional Neural Networks (CNN)]]
	- [[Autoencoder]]
	- ...

## Perceptron


- As <mark style="background: #FFB86CA6;">perceptron</mark>: $y = \Phi(w^\top x + b)$
	- Input are weighted by $w$ summed up
	- $b$ is bias
	- $\Phi$ is the activation function

## Multi-layer perceptron

- perceptrons are ordered in a directed graph 
	- most of the time ordered into layers
	- ![[Pasted image 20231113162105.png |300]]
	- if acyclic its a <mark style="background: #FFB86CA6;">Feed-forward neural network</mark>
- weights for the transition of one layer to another can be put into a weight matrix $\Theta$
- Loss function $J = \frac{1}{2m} \sum(f^i - c^i)^2$ wehre $f$ is the result of the network and $c$ is the label of the data 
	- use [[Gradient Descent]] and [[Backpropagation]] to optimize the weights


## Activation function

- Should be non-linear, otherwise all layers can be combined into one
- Should have large gradients so that the overall gradient does not approach 0 too quickly
- Should be centered around 0, which simplifies initialisation
![[Pasted image 20231113181526.png]]
- <mark style="background: #FF5582A6;">Sigmoid usually very poorly suited</mark>
- <mark style="background: #BBFABBA6;">ReLU variants empirically very good</mark>

## Hyperparameters

- see [[Hyperparameters]]
- activation function
- number of layers and number of perceptrons per layer
- learning rate of the gradient descend

---

Origin: 
References: [[Machine Learning Index]]
Tags: 
Created: 13.12.2025