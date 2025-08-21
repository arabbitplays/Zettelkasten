# Path Tracing

- like [[Distributed Raytracing]] but with $N=1$ (the ray never splits)
	- converges to the true solution because through [[Anti Aliasing]] multiple primary rays are generated
- improve [[Monte Carlo Integration]] by choosing sampling direction more sophisticated (see [[Importance Sampling]] and [[Multiple Importance Sampling (MIS)]])
	- always remember to divide out the chance to pick a certain direction
- Other techniques:
	- [[Russian Roulette]]

---

Origin: Computergrafik
References: [[Zettelkasten/🟢Permanent/Raytracing|Raytracing]]
Tags: 
Created: 19.11.2024

