# Monte Carlo Integration

- approximate integral by evaluating the integrant at $N$ uniform random samples $x_i \in [a,b]$
$$\int_a^b f(x) = \frac{b-a}{N} \sum_i^N f(x_i)$$
- converges more quickly if the PDF is similar to the integrant (ergo not uniform in the general case)
$$\int f(x)dx = \frac{1}{N}\sum_i^N \frac{f(x_i)}{p(x_i)}$$
- the RMSE of a unbiased estimator should decrease in s straight line on a double log scale
		
---

Origin: Computergrafik I
References: 
Tags: 
Created: 19.11.2024

