# Intrusion Detection

## Introduction

- detecting attacks to hosts and networks, often done by an <mark style="background: #FFB86CA6;">Intrusion Detection System (IDS)</mark>
	- monitors a stream of events (from the host, network or application) 
	- analyzes through the signatures or with machine learning
	- and reacts with reporting, blocking or sand-boxing

## Detection through signatures

- write regular expressions that search for known attacks
![[Pasted image 20251117115237.png]]
- has nearly no false positives
- doesn't scale well with different kind of attacks
- can not react to novel attacks

## Detection through machine learning

- feature extraction from the monitored events
	- numerical features like length of the request, number of newlines, entropy, ...
	- string features, mapping string or n-grams to a feature space (see also [[Natural Language Understanding#Representation]])
	- structural features, like the parse tree of a HTTP request
		- mapping between feature space and all possible sub-trees
- for the detection, different kinds of models can be trained
	- modelling the malicious activity -> like detection through signatures
	- modeling of benign behaviour -> <mark style="background: #FFB86CA6;">anomaly detection</mark>
		- Unsupervised learning as there is only on class
		- anomalies $\neq$ attacks
	- or learn the difference of the two -> classification

### Modelling normality

- events used for training are not labled -> $x_1, x_2, \dots, x_n \in X$ 
- events are mapped to feature space through $\phi(x)$

1. center of mass -> place one hyper-sphere at the center of mass
	- $\mu = \frac{1}{n}\sum \phi(x_i)$
	- anomaly score is the distance to $\mu$
2. center of neighborhood -> basicaly [[Clustering]]
	- anomaly score is the distance to the closest center
3. <mark style="background: #FFB86CA6;">One-class Support Vector Machines (SVMs)</mark>
	- finds the minimum hypersphere enclosing the data
	- made robust against outliers through regularisation

$$min_{\mu, R}\ R^2$$ $$with \ ||\phi(x_i)-\mu|| ^2 \leq R^2\ for\ all\ i$$
- regularisation through slack variables $\xi_i$ 
	- small $C$ is a smooth boundary, large C is a firm decision boundary
	- the $\xi_i$ are learned and are constrained to $\xi_i \geq 0$
$$min_{\mu, R, \xi}\ R^2+C \sum \xi_i$$
$$with \ ||\phi(x_i)-\mu|| ^2 \leq R^2+\xi_i\ for\ all\ i$$
![[Pasted image 20251117123150.png | 300]]

---

Origin: 
References: 
Tags: 
Created: 17.11.2025

