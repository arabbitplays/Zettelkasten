# Kernels in ML

## Introduction

- Used to map high dimensional arbitraty objects to a feature space  
  
- Symmetric  
- Positive semi-definite $\sum c_i c_j k(x_i, x_j)$ for arbitrary $c_i, c_j$  
  
- Induces a mapping $k(x, z) = \langle \phi(x), \phi(z) \rangle$  
- And a distance measurement
$$|| \phi(x) - \phi(z) ||_2 = \sqrt{ k(x, x), k(z, z) - 2 k(x, z) }$$

## Hashing kernels

- specialized kernels can be hard to handle
- use a hashing function $H$ to has a set of features $B$
	- $B$ can be bag of words for example

$$k(x, z) = \sum_{b\in B} occ(H(b), x')\ occ(H(b), z'), x' = \{H(b) | b \in x\}$$

---

Origin: 
References: 
Tags: 
Created: 27.02.2026

