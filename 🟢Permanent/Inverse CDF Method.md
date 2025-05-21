# Inverse CDF Method

## Introduction

- Method to generate a random variable according to a given probability density function (PDF)
	- if the PDF is large in a region, we want to probability to take a sample there to be high too
- the distribution function (CDF) must be invertable and a pseudo random number generator is given to generate uniformly distributed random variables

## 1 Dimension

1. Determine the CDF $F(x)=\int_{-\infty}^x p(t)dt$ 
2. Invert the CDF
3. generate uniformly distributed $\xi \in [0, 1)$ 
4. $X = F^{-1}(\xi)$ is the distributed according to $p$

![[Pasted image 20250520114733.png | 300]]

### Example
	
$$p(x) = 2x, x \in [0, 1)$$
$$F(x) = \int_0^x 2tdt = [t^2]_0^x = x²$$
$$X = \sqrt{\xi}$$
## Multi-Dimension

- Given a $p(x,y)$ with $x \in [x_l, x_h]$ and $y \in [y_l, y_h]$
1. calculate $F(x, y_h) = \int_{x_l}^x \int_{y_l}^{y_h} p(x', y')dy'dx'$
2. $\xi_1 = F(x, y_h)$
3. calculate $F(y | x) = \int_{y_l}^y p(x, y')dy' / \int_{y_l}^{y_h} p(x, y')dy'$
	1. if $p$ can be written as $f(x)g(x)$ then $F(y|x) = F(x,y) / F(x, y_h)$
4. $\xi_2 = F(x,y) / F(x, y_h)$

### Example

see [[Disk Sampling]]

---

Origin: 
References: 
Tags: 
Created: 20.05.2025

