# Metropolis Light Transport

## Introduction

- a category of rendering algorithms for physical-based offline rendering
- a lot of [[Path Tracing]] algorithms struggle to render SDS paths, as it is really hard to find these complex light paths
	- but they find them sometimes
- most rendering algorithms can be expressed is [[Path Space]] and use [[Monte Carlo Integration]] to solve the integral over the measurement contribution function
	- basic idea: use a conditional transition probability $T(Y|X_i)$ to sample a path based on a "good" path 
	- the PDF for the new path $Y$ is then $p(X_i)T(Y|X_i)$ integrated over all $X_i$
	- to solve this, markov chains are used

## Metropolis-Hastings Algorithm

- Goal: steer a random walk of conditional PDF to a specific target equilibrium distribution $f(x)$
	- we can only point sample $f$, no integration and no inversion

- choose a $y$ is the state space uniformly
- accept $x_{i+1} = y$ with the <mark style="background: #FFB86CA6;">acceptance probability</mark> $$a = \frac{f(y)}{f(x_i)}$$
	- $y$ is called the <mark style="background: #FFB86CA6;">tentative sample</mark>
	- $x_i$ is called the <mark style="background: #FFB86CA6;">current sample</mark>
- the histogram representing how often a state is reached converges to $f$

- we don't want to uniformly sample the state space but use mutations instead $P(x_{i+1} | x_i) = a(x_i \rightarrow y) T(y | x_i)$
	- to still reach the right target distribution, a specific $a$ is needed that fulfills <mark style="background: #FFB86CA6;">detailed balance</mark> $$f(x_i)T(y|x_i)a(x_i \rightarrow y) = f(y)T(x_i|y)a(y \rightarrow x_i)$$
- for example $$a(x_i \rightarrow y) = min \left(1, \frac{f(y) / T(y | x_i)}{f(x_i)/T(x_i|y)} \right)$$

## Application for light transport

- use the path space as the state space
- the pixels are the histogram, normalized by the mean image brightness

1. Generate initial path $X_0$ (for instance via [[Bidirectional Path Tracing | BDPT]])
2. Mutate with transition probability density $T(Y|X_i)$
3. Accept $X_{i+1}=Y$ with probability $a(X_i→Y)$
4. Otherwise keep $X_{i+1}=X_i$
	- in both cases increase i
5. Accumulate mean image brightness $b$ at pixel determined by $X_i$
6. Repeat from 2.

- since $X_0$ is sampled from another distribution and $f$ is not converged yet, there is a <mark style="background: #FFB86CA6;">startup bias</mark>
	- can be ignored
	- or initial samples are discarded
	- or the initial candidates are resampled after the convergence
- what are good mutations to use?
- <mark style="background: #FFB86CA6;">ergodicity</mark> must be fulfilled - every state of the state space can be reached

## Veach Style MLT

- Veach proposed 4 mutation strategies
	- transition probabilities is [[Measure and Measure Space | Vertex Area Measure]], resulting together with the measurement contribution in a acceptance probability $a$
- <mark style="background: #FFB86CA6;">Lens perturbation</mark>
	- perturb outgoing direction from the eye
		- PDF of $x_2$ by $T(Y|X)=p(\omega)G(x_1, x_2)$ 
	- ![[Pasted image 20260320150035.png | 300]]
- <mark style="background: #FFB86CA6;">Caustic perturbation</mark> 
	- perturb outgoing direction from vertex $x_3$
		- PDF of $x_2$ by $T(Y|X)=p(\omega)G(x_3, x_2)$ 
	- ![[Pasted image 20260320150205.png | 300]]
- <mark style="background: #FFB86CA6;">Multi-chain perturbation</mark>
	- perturb multiple directions along the path
	- transition consists of multiple vertex PDFs
	- ![[Pasted image 20260320150344.png | 350]]
- <mark style="background: #FFB86CA6;">Bidirectional perturbation</mark>
	- Least efficient mutation type: replace sub-paths (or the whole path) using BDPT
	- Required for ergodicity! Can only reach right side by simultaneously replacing two vertices
	- ![[Pasted image 20260320150611.png | 300]]

- a very flexible framework for designing mutations and exploring effects locally
- but very hard to implement, as getting the transition pdfs right is very non-trivial

## Kelemen MLT

- the idea is to only mutate the random numbers used to construct the paths
- the <mark style="background: #FFB86CA6;">primary sample space</mark> is the space of random numbers $[0, 1)^s$ 
- only two mutations:
	- large step: pick a completely independent new $\xi$ (for ergodicity)
	- small step: $(\xi + \zeta) \text{ mod } 1$ with $\zeta \in [-m, m]^s$ for a small $m$
- the is the symmetry $T(\xi_i | \xi_{i+1}) = T(\xi_{i+1}, \xi_i)$ is primary sample space
	- NOT is path space
- through that, the acceptance probability simplifies to $a(x \rightarrow y) = min(1, \frac{C_y}{C_x})$, where $C$ is the pixel contribution of the normal MC estimator which we calculate anyways
- not as optimally adapted as Veach style, but way easier to implement

---

Origin: 
References: [[Path Space]] [[Path Tracing]] [[Rendering Index]]
Tags: 
Created: 19.03.2026

