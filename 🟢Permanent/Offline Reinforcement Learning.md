# Offline Reinforcement Learning

## Preliminaries
[[Reinforcement Learning]]
- V-function - how good is it to be in state $s$ under policy $\pi$
$$V(s) = \mathbb{E}_\pi [\sum_k \gamma^k r_{t+k} |s_t = s]$$
- Q-function - how goo dis it to take action $a$ in state $s$ under policy $\pi$
$$Q(s, a) = \mathbb{E}_{a' \sim \pi(a' |s')}[r + \gamma Q(s', a')]$$
- Advantage function - how good is it to take the action $a$ in state $s$ compared to the average action in state $s$ 
$$A(s,a) = Q(s,a) - V(s)$$

- <mark style="background: #FFB86CA6;">On-policy RL</mark> - classical RL, using data from only the current policy
	- <mark style="background: #FF5582A6;">Slow convergence, not data efficient</mark>
	- <mark style="background: #BBFABBA6;">Good results after convergence</mark>
- <mark style="background: #FFB86CA6;">Off-policy RL</mark> - Use transition from any policy, use a replay buffer for the policy update
	- $D_{buf} \leftarrow D \cup hist(D_{buf}),\ hist(D_{buf}) \subseteq D_{buf}$
	- <mark style="background: #BBFABBA6;">More data efficients, faster convergence</mark>
	- <mark style="background: #FF5582A6;">Not as good as On-policy</mark>

## Offline-RL

- Similar setting to [[Imitation Learning]] with a demonstrator that interacts with the environment and generates trajectories of length $T$
	- But there is also a reward function -> more information to<mark style="background: #D2B3FFA6;"> separate good and bad parts of demonstrations</mark>
![[Pasted image 20240811142545.png |500]]
$$\pi^* = arg\ max_\pi \sum_t^T \mathbb{E}_{s_t \sim \rho_\pi(s),\ a_t \sim \pi(a_t | s_t)}[\gamma^t r_t]$$

## Policy Constraints

- A problem is [[Covariate Shift]] and that the learned policy tends to drift apart from the behaviour policy
	- Bound the policy by some constraints
	- bound should not be too pessimistic or the learned policy can't be better than the behaviour policy but also pessimistic enough to not allow for significant differences in some states

### Explicit constraints
- Fit a proxy policy to the samples (through [[Imitation Learning#Behavioral Cloning]]) and use $KL(\pi || \pi_b) \leq \epsilon$
	- Support constraint with $\pi(a | s) > 0 \Leftrightarrow \pi_b(a|s) \geq \epsilon$
- How to implement the constraints
	- In the policy update step through Lagrange Multiplier $\lambda$ (as a meta parameter or optimization algorithm)
		- $\pi_{new}(a | s) = \dots - \lambda KL(\pi ||\pi_b)$
	- Or directly in the reward function
		- Punishes actions that violate the constraints or lead to constraint violations
		- $r_{Diff}(s, a) = r(s,a) - Diff(\pi, \pi_b)$

### Implicit constraints
- Formulate the constraints in a way that only needs the samples, not the behaviour policy
	- Behaviour policy is estimated with [[Schätzer#Maximum-Likelihood-Schätzer]]

### Expectile regression

- Punish negative errors harder than positive ones
- ![[Pasted image 20240811144948.png |400]]


---

Origin: 
References: 
Tags: 
Created: 10.04.2026

