# Bidirectional Path Tracing

## Introduction

- idea: combine [[Path Tracing]] and [[Light tracing]]
- sample a light and an eye subpath and combine them through shadow rays to full paths
- because the connection is deterministic, it does not result in a PDF
- so the PDF of a full path is
$$p(X) = \prod p(e_i) \prod p(l_i)$$

## Multiple Importance Sampling

- consider all possible combinations of subpath to form a full path
- all of these combinations are different sampling techniques for a full path 
	- weight them with [[Multiple Importance Sampling (MIS) | MIS]] 
	- for a path of length 7 we get 7 techniques, 6 possible connections and one pure path intersecting the light by chance
![[Pasted image 20260123104504.png]]


---

Origin: 
References: 
Tags: 
Created: 23.01.2026

