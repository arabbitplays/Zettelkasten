# Path Tracing

- like [[Distributed Raytracing]] but with $N=1$ (the ray never splits)
	- converges to the true solution because through [[Anti Aliasing]] multiple primary rays are generated
- improve [[Monte Carlo Integration]] by choosing sampling direction more sophisticated
	- always remember to divide out the chance to pick a certain direction

## Light Importance Sampling

- with a chance, send a shadow ray directly to a random point in a random light source
- don't add the emitted light term when hitting a light source by chance

---

Origin: Computergrafik
References: [[💡Resources/📦Zettelkasten/🟢Permanent/Raytracing]]
Tags: 
Created: 19.11.2024

