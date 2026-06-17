# Wave VII - Learning from Experience

## Introduction

- main research focus since 2016, driven by growing complexity and uncertainty
- use [[Reinforcement Learning]] to learn a system instead of trying to model it

- similar setup as traditional [[MAPE-K]]
	- state - abstracts system conditions and environment context
		- may be partial, noisy or incomplete
	- actions - adaptations and reconfiguration options
	- reward - feedback, reflecting performance, cost, resource usage, ...
	- policy - which action to take in a given situation
		- can be deterministic or stochastic
- optimize long-term accumulated reward
- should work together with classic models and fill the gaps where they are weak
![[Pasted image 20260409144306.png]]

- pros
	- can reduce modeling effort
	- better handling of dynamic environments
- cons
	- unpredictable behavior especially during learning
	- hard to assure correctness
	- designing a reward is hard

## Choosing RL approaches

- for SAS, algorithm should learn at runtime
- Value vs policy based
	- for configuration selection (discrete) use value-based
	- for parameter tuning use policy based
- model-based vs model free
	- dependent on how knowledge intense the adaptation is
- exploration vs exploitation
	- exploration is a design risk and should be explicitly governed by the architecture
- explainability and trust
	- value-based methods often easier to explain
- safety and guarantees
	- risks are constraint violations and oscillations
	- use hybrid approaches and restricted action sets

- Decision Heuristics
	- Discrete actions + high explainability needed → Start value-based, tabular/linear; add DQN if scale grows
	- Continuous control + fast but safe updates → Actor–critic (PPO/A2C) with shields and small step sizes 
	- Tight safety & predictability → Model-based planning/simulation; online MBRL with conservative exploration
	- Rich logs/simulators available → Prefer off-policy (DQN/TD3/SAC), validate offline, then gated rollout
	- Limited compute budget → Lightweight models, offline pretraining, scheduled updates during low load

## Bayesian Estimator

- can be used to keep runtime models accurate
- improves model parameters sequentially as new data arrives
	- data already known about the modle is called <mark style="background: #FFB86CA6;">prior</mark>
	- new data coming in is the <mark style="background: #FFB86CA6;">posterior</mark>
- builds again inherently on Markov chains (see [[Variable Based Models]])
- ![[Pasted image 20260416141829.png]]o

## Temporal difference learning

- used to learn to select optimal plans from a big range of possiblities
	- many possible connections
	- load dependent quality indicators
- use RL to try out different configuration, use the QoS indicators as a reward 

## Fuzzy Q-Learning

- in the context of scaling rules in a cloud infrastructure
	- workloads change, optimization of resource usage to save costs while also providing a stable service
- input current workload, average response time, scaling rules and fuzzy membership functions
- output incremental or decremental scaling

- fuzzy membership functions convert some metric to a fuzzy mix of states
	- workload is categorized into low, medium and high
	- ![[Pasted image 20260416145243.png | 300]]
	- response time is categorized into good, ok and bad
	- ![[Pasted image 20260416145307.png | 300]]

- scaling rules convert membership function output to adaptations
	- if (w is low) AND (r is good) THEN (sa = -2)
	- if (w is medium) AND (r is ok) THEN (sa = 0)
	- ...

- <mark style="background: #FFB86CA6;">fuzzy logic controller</mark>
	- calculates the outputs of all scaling rules times the change they demand and adds them together
	- round to nearest integer to get a defuzzied result
	- assumes that all rules are given
- <mark style="background: #FFB86CA6;">fuzzy q-learning</mark>
	- RL that learns the scaling rules at runtime

---

Origin: [[Self-adaptive Systems.pdf]]
References: 
Tags: 
Created: 09.04.2026

