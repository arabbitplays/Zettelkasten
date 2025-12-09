# Lambert Diffuse

## Introduction

- perfect diffuse reflection, so it is totally independent of the viewing direction
- reflects a certain ratio $\rho$ from the incoming light, called the <mark style="background: #FFB86CA6;">albedo</mark> 

- starting from energy conservation:
$$\begin{align}
\rho &= \int f_r L_i(\mathbf{x}, \omega_i)\cos\theta_i\mathrm{d}\omega_i\\
   &= f_r \cdot \int 1 \cdot \cos\theta_i\mathrm{d}\omega_i\\
   &= f_r \cdot \pi\\
\Rightarrow f_r(\omega_o,\omega_i) &= \frac{\rho}{\pi}\\
\quad
\end{align}$$

- this is the diffuse component of the [[Phong Lighting Model]]
- just by itself, it is physically plausible

---

Origin: 
References: [[Bidirectional Scattering Distribution Function (BSDF)]]
Tags: 
Created: 04.12.2025

