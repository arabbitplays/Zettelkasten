# Machine Learning in Computer Graphics

## Introduction

- used to speedup the evaluation of complex [[Signed Distance Field (SDF)]]s or to get the behavior of them given a given voxel grid
	- either use an existing SDF as the ground truth
	- or a discrete voxel grid storing the distance to the next surface (if a full SDF is to complex to aquire)
- they have a fixed size in memory given the network architecture
	- breaks the curse of dimension at least a bit

## Regularisation

- is similar to classical [[Regularisierung]] in machine learning
- how to fill in gaps of the training data and avoid overfitting
- express knowledge of our problem domain by modeling an extra term $P(x)$ and a weight parameter $\lambda$
$$argmin_x |y-F(x)| + \lambda P(x)$$
- what are good terms for that job? 
	- <mark style="background: #FFB86CA6;">Total Variantion</mark> - $TV(f) = \int |\nabla f(x)|dx$
		- weight rare strong steps ar the edges vs. uniform minor changes
	- other domain specific terms

## Input Encoding

- is very important for the final outcome
- the embedding of the input can be learned too

---

Origin: 
References: [[Neuronale Netze]], [[Signed Distance Field (SDF)]]
Tags: 
Created: 08.07.2025

