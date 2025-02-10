# Distributed Raytracing

- nutze [[Monte Carlo Integration]] um die [[Rendering Equation]] zu lösen
	- $2\pi$ ist die Oberfläche einer Halbkugel
$$L(x, \omega)=L_e(x, \omega)+\frac{2\pi}{N}\sum_i^N f_r(\omega_i, x, \omega)L_i(x, \omega_i)cos(\Phi_i)$$

## Erzeugung zufälliger Richtungen

- zwei uniforme Zufallszahlen $\xi_i, \xi_2 \in [0, 1)$
$$\theta = arccos(1-2\xi_1)\ \ \ \phi=2\pi \xi_2$$
$$w_i = (sin(\theta) \ cos(\phi), sin(\theta)\ sin(\phi), cos(\theta))$$

---

Origin: Computergrafik I
References: [[💡Resources/📦Zettelkasten/🟢Permanent/Raytracing]] [[Rendering Equation]]
Tags: 
Created: 19.11.2024

