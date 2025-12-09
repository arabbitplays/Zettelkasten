# Fresnel Equations

## Introduction

- equations derived from Maxwells equations, describing how flux is distributed between reflection ($R$) and transmission ($T = 1 -R$)
- every [[Materials | material]] has a complex valued <mark style="background: #FFB86CA6;">index of refraction (IOR)</mark> $N(\lambda) = \eta(\lambda) + i\kappa(\lambda)$ 
	- this is dependent on the wavelength $\lambda$ 
	- $\eta$ is the simple IOR and describes how much light slows down in the material
	- $\kappa$ is the absorption coefficient (relevant for metals, in dielectrics it is $0$)
- the direction of transmission is determined through [[Snells Law of Refraction]]
	- from optical denser material to optical thin material, <mark style="background: #FFB86CA6;">total internal reflection</mark> can happen, where $R = 1$
## Formula

- two parts, for parallel polarised light $R_p$ and orthogonal polarised light $R_s$ 
	- most renderers are unpolarised, so only $R$ is relevant
$$R_s = \left| \frac{N_1\cos_r - N_2\cos_t}{N_1\cos_r + N_2\cos_t} \right|^2$$
$$R_p = \left| \frac{N_1\cos_t - N_2\cos_r}{N_1\cos_t + N_2\cos_r} \right|^2$$
$$R = (R_s + R_p)/2$$
$$\cos_t = \sqrt{1 - \left(\frac{N_1}{N_2}\right)^2(1-\cos_r^2)}\qquad$$
- <mark style="background: #D2B3FFA6;">this cosine is in general complex valued!</mark>

---

Origin: 
References: 
Tags: 
Created: 04.12.2025

