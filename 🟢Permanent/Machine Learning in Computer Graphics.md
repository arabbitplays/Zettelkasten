# Machine Learning in Computer Graphics

## Introduction

- used to speedup the evaluation of complex [[Signed Distance Field (SDF)]]s or to get the behavior of them given a given voxel grid
	- either use an existing SDF as the ground truth
	- or a discrete voxel grid storing the distance to the next surface (if a full SDF is to complex to aquire)
	- fit a number of observations from different angles
- they have a fixed size in memory given the network architecture
	- breaks the curse of dimension at least a bit
- another possible application is calculating a radiance field
	- how much light travels at any point in any direction
	- can use normal [[Ray Marching]] techniques to render those
		- alternatively use Gaussian Splatting to render them

## Regularisation

- is similar to classical [[Regularisierung]] in machine learning
- how to fill in gaps of the training data and avoid overfitting
- express knowledge of our problem domain by modeling an extra term $P(x)$ and a weight parameter $\lambda$
$$argmin_x |y-F(x)| + \lambda P(x)$$
- what are good terms for that job? 
	- <mark style="background: #FFB86CA6;">Total Variantion</mark> - $TV(f) = \int |\nabla f(x)|dx$
		- measure of how much the function changes over the whole domain
		- weight rare strong steps at the edges vs. uniform minor changes
	- other domain specific terms

## Input Encoding

- is very important for the final outcome
- the embedding of the input can be learned too

---

Origin: 
References: [[Neural Networks]], [[Signed Distance Field (SDF)]]
Tags: 
Created: 08.07.2025

