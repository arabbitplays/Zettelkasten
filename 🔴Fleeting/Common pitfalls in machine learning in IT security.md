# Common pitfalls in machine learning in IT security

## Introduction


## Sampling Bias

- the collected data does not sufficiently represent the real-world distribution of the underlying security-problem

- define target distribution as specific as possible
- how to check if a training and a test distribution is the same
	- try to train a classifier trying to distinguish between test and training data

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
	- for example a detextor is evaluated with different hyper parameters on one test set, and then the best are reported

- fix hyperparameters at training time

## Inappropriate Baseline

- no comparison with simpler ML or non ML solutions
	- maybe the computational overhead of a deep-learning model is not needed

## Inappropriate Performance Measures

## Base Rate Fallacy

- a large class inbalance is ignored when interpreting the performance measures

## Lay-Only Evaluation

- approach is only evaluated in an artificial environment, without discussing practical limitations

- closed-world systems may have limited diversity
- consider runtime and storage constraints
- ideally, deploy in a real-world environment

## Inappropriate Threat Model

- the security of machine learning itself is not considered, exposing the system to a variety of attacks

- consider adaptive ad1verseries

---

Origin: 
References: 
Tags: 
Created: 08.12.2025

