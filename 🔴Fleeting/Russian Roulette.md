# Russian Roulette

- A method for improving the efficiency of [[Monte Carlo Integration]] on [[Path Tracing]]
- if a integrand has the form $f(X)v(X)$ where $f$ is cheap to evaluate and $v$ is expensive (for example BRDf and the visibility of a light source), the calculation of $v$ can be skipped if $f(X) = 0$
- skipping it if $f(X)$ is very low would result in a biased estimator, always underestimating the brightness of the point

- choose a termination probability $q$ of a path 
	- can be arbitrary but should be chosen 

---

Origin: 
References: [[Path Tracing]]
Tags: 
Created: 05.03.2025

