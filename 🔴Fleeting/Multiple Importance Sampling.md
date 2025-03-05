# Multiple Importance Sampling

- Variance reduction technique for [[Monte Carlo Integration]]
- it is a common case that an integrand has the form $f_a(x)f_b(x)$ where [[Importance Sampling]] techniques exists for both factors ($p_a$ and $p_b$) but not for the product
- both techniques may be good in some cases, but bad in others, so sampling only with one can leave the estimator with the variance of the other
- multiple importance sampling builds on the idea that all distributions are sampled and then weighted to prevent variance spikes from mismatched between the integrand's value and the sampling technique
$$w_a(X)\frac{f(X)}{p_a(X)} + w_b(Y)\frac{f(Y)}{p_b(Y)}$$

## Weighing Functions

- sampling both and taking the average is bad because once variance is introduced, adding it so a low variance sample doesn't change anything
- The weight should be big if the integrator and the used technique are a good match
- The <mark style="background: #FFB86CA6;">Balance heuristik</mark> tries to achieve this by considering all ways a sample could have been generated
$$w_i(X) = \frac{n_ip_i(x)}{\sum n_j p_x(x)}$$


---

Origin: https://pbr-book.org/4ed/Monte_Carlo_Integration/Improving_Efficiency#sec:multiple-importance-sampling
References: 
Tags: 
Created: 05.03.2025

