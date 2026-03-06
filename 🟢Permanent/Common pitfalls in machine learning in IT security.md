# Common pitfalls in machine learning in IT security

## Sampling Bias

- the collected data does not sufficiently represent the real-world distribution of the underlying security-problem

- define target distribution as specific as possible
- how to check if a training and a test distribution is the same
	- try to train a classifier trying to distinguish between test and training data

## Label Inaccuracy

- wrong, unstable or inaqurate labels can hurt the performance of classifiers
- but unsure labels should also not be removed to not have a sampling bias

- reduce impact of noisy labels by 
	- modelling noise actively (for example through confidence scores)
	- clean labels by human hand or by letting multiple models agree
	- use a robust loss function
## Data Snooping

- models are trained with data, that is usually not available in practice
	- happens in very subtle ways, 
		- like ignoring the temporal relationship of the data (model is evaluated on data that preceeds the training data -> thats kinda knowledge of the future
		- removing outliers with statistics over the whole dataset -> can't be done in practice

- split test data very early in development
- consider temporal relationship, test on newer data

## Spurious Correlations

- Artifacts unrelated to the problem can be used as a shortcut to separate classes -> models learns these shortcuts, not solving the actual task

- [[Explainable AI (XAI)]] can mitigate this problem

## Biased Parameter Selection

- the final parameters of a learning-based method are not fixed at training time -> they indirectly depend on the test set
	- for example a detector is evaluated with different hyper parameters on one test set, and then the best are reported

- fix hyperparameters at training time

## Inappropriate Baseline

- no comparison with simpler ML or non ML solutions
	- maybe the computational overhead of a deep-learning model is not needed

- always compare against the state-of-the-art, a non ML solution and simple models

## Inappropriate Performance Measures

- the chosen performance measure does not account for the constraints of the real application scenario
	- for example a 99% accuracy might still be very bad if only 1% of the traffic is malicious

- consider practical deployment, as the best performance measure is highly application specific
- in applications with highly unbalanced datasets, precision and recall is recommended
	- precision: how often were alerts correct: $\frac{TP}{TP+FP}$
	- recall: How much malicious activity did we catch: $\frac{TP}{TP + FN}$

## Base Rate Fallacy

- a large class inbalance is ignored when interpreting the performance measures
	- with a deceptively low LPR, enough FP can happen to make the system useless in practice
- is about interpretation of measures, while the last point is about the wrong description of performance

## Lab-Only Evaluation

- approach is only evaluated in an artificial environment, without discussing practical limitations

- closed-world systems may have limited diversity
- consider runtime and storage constraints
- ideally, deploy in a real-world environment

## Inappropriate Threat Model

- the security of machine learning itself is not considered, exposing the system to a variety of attacks

- consider adaptive adverseries and white box attacks adhering to Kerckhoffs' principle

---

Origin: 
References: 
Tags: 
Created: 08.12.2025

