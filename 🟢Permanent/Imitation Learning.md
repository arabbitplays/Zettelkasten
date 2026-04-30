---
date created: 29.05.2024 11:50
date modified: 13.08.2024 15:13
---
# Imitation Learning

## Introduction

- Really similar to [[Reinforcement Learning]], but instead of a reward function we have a set of demonstrations $D = \{\tau_1, \dots\}, \tau_n = ((s_1, a_1), \dots)$ and learn the policy from that

## Behavioral Cloning

- Fit the behaviour of the agent $\pi_\theta(a_t | s_t)$ to the behaviour of the demonstrators $\pi_{dem}(a_t|s_t)$ 
	- Calculate difference with Kullback–Leibler divergence https://en.wikipedia.org/wiki/Kullback%E2%80%93Leibler_divergence
$$arg\ min_\theta\ \mathbb{E}_{\rho_{dem}(s)}[D_{KL}(\pi_{dem}(a_t | s_t)\ ||\ \pi_\theta (a_t |s_t))]$$
- Is basically [[Neural Networks| Supervised learning]]
- Problem: [[Covariate Shift]]
- <mark style="background: #FFB86CA6;">DAgger: Dataset Aggregation</mark>
	- ![[Pasted image 20240529120858.png |200]]
	- Add the new trajectory to $D$
- <mark style="background: #FFB86CA6;">Learning from Play</mark>
	1. Create arbitrary demonstrations with some demonstrators
	2. Define tupels of partial demonstrations and the last state of if (flags)
	3. Use the Tupels as the dataset
	4. ![[Pasted image 20240529122228.png |300]]
- <mark style="background: #FF5582A6;">Expert data is expensive</mark>
- <mark style="background: #FF5582A6;">Demonstrations are an upper bound for the performance</mark>

## Inverse Reinforcement Learning

- Don't optimize for the demonstrations but for the goal of the demonstrator
	- Learn the underlying reward of the demonstrations and then a policy for this reward
	- Problem is ambiguous because demonstrations can be produced by multiple policies or policies are optimal for multiple rewards
- Maximize the entropy of the policy to have few assumptions
- <mark style="background: #FF5582A6;">Has a los of assumptions to make it work</mark>
	- Learned Rewards are linear in the features
	- Trajectory distribution is exponential which assumes a Boltzmann rational expert
	- Only works well in deterministic environments
	- Expensive
	- Still bounded by the quality of the demonstrations

## Adversarial Methods

- Compare the agent with the demonstrations, if you can't see the difference, it is good
	- training a binary classifier to distinguish the trajectories
- Instead of matching the policies between demonstrator and agent, match the state-action occupancy
	1. sample trajectories from the current policy
	2. update discriminator with demonstrations and agent trajectories
	3. do a RL policy step with cost based on discriminator
- Perform bad in multi-modal scenarios, wit h few data and chancing dynamics

## Learning with Human Data

- <mark style="background: #FFB86CA6;">Trajectory-ranked reward Extrapolation (T-Rex)</mark>
	- Leverage additional information from suboptimal demonstrations
	- Rank the demonstrations pair wise and extrapolate 

### Learning from Play

- <mark style="background: #BBFABBA6;">Play data is cheap, general (functionally and transitionally) and rich in exploration</mark>
- <mark style="background: #FF5582A6;">Play data is unlabeled (unknown purpose), multi-modal and sub-optimal</mark>
- Just learn to recognize the plans of the play data
	- <mark style="background: #FFB86CA6;">Plan recognition network</mark> - Input the whole data, output parameters of a latent plan distribution
	- <mark style="background: #FFB86CA6;">Plan proposal network</mark> - Input current state and final goal, output parameters of a latent plan distribution
	- <mark style="background: #FFB86CA6;">Action decoder network</mark> - Input current state, final goal and sampled plan, output next action
	- Use KL-divergence between the output of the plan recognition and the plan proposal to learn

## Behaviour transformers

- <mark style="background: #BBFABBA6;">Good to leverage multi-modal performance</mark>
- Binning of the continous action space with k-means

---

Origin: 
References: 
Tags: 
Created: 10.04.2026

