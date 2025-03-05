# Russian Roulette

- A method for improving the efficiency of [[Monte Carlo Integration]] on [[Path Tracing]]
- if a integrand has the form $f(X)v(X)$ where $f$ is cheap to evaluate and $v$ is expensive (for example BRDf and the visibility of a light source), the calculation of $v$ can be skipped if $f(X) = 0$
- skipping it if $f(X)$ is very low would result in a biased estimator, always underestimating the brightness of the point

- choose a termination probability $q$ of a path 
	- can be almost arbitrary, for example an estimate of the value of the integrand for the chosen sample direction
- if the path is not terminated, weight the result by $1/(1-q)$ to compensate the terminated paths

---

Origin: 
References: [[Path Tracing]]
Tags: 
Created: 05.03.2025

