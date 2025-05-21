# Disk Sampling

## Introduction

The goal is to uniformly sample a disc with radius $R$ using the [[Inverse CDF Method]]
$$r = R\sqrt{\xi_1}$$
$$\theta = 2 \pi \xi_2$$

## Derivation

- The naive sampling method with $r = R\xi_1$ is not a uniform distribution!

$$p(r, \theta) = \frac{1}{\pi R^2}$$
$$F(x,y)= \int \int p'(x',y')dy'dx'$$
Go to polar coordinates with $dy'dx' = dA = r\ dr\ d\theta$
$$F(r, \theta) = \int_0^\theta\int_0^r p(r', \theta') r'\ dr'\ d\theta' = \frac{r^2 \theta}{2 \pi R^2}$$
$$\xi_1 = F(r, 2\pi) = \frac{r^2}{R^2} \Leftrightarrow r = R \sqrt{\xi_1}$$
$$\xi_2 = \frac{F(r, \theta)}{F(r, 2\pi)} = \frac{\theta}{2 \pi} \Leftrightarrow \theta = 2\pi\xi_2$$
---
---

Origin: 
References: 
Tags: 
Created: 20.05.2025

