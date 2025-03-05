# Multiple Importance Sampling

- Variance reduction technique for [[Monte Carlo Integration]]
- it is a common case that an integrand has the form $f_a(x)f_b(x)$ where [[Importance Sampling]] techniques exists for both factors but not for the product
- both techniques may be good in some cases, but bad in others, so sampling only with one can leave the estimator with the variance of the other
	- sampling both and taking the average is also bad because once variance is introduced, adding it so a low variance sample doesn't change anything

---

Origin: https://pbr-book.org/4ed/Monte_Carlo_Integration/Improving_Efficiency#sec:multiple-importance-sampling
References: 
Tags: 
Created: 05.03.2025

