# Radiance Transfer Equation

## Introduction

- one equation describing how light behaves in any volume of space, espacially in participating media
- this is not meant for direct implementation but it is the physical base equation for every fotorealistic rendering algorithm
## Simplifying Assumptions

- geometric optics -> light behaves as a particle, not a wave
- speed of light is instant
- no relativistic effects, no effect of gravity
- light travels along straight lines (piecewise constant IoR)
- only elastic scattering (wavelength is oerserved, no fluorecense)
- no light polarisation

## Derivation of the base form from first principles

- we measure photons in the 5D phase space $V\times \Omega$ describing the position and direction of photons
- the flow of photons results in an equilibrium that will be described here
- three effects change the observed amount of light:
	- <mark style="background: #FFB86CA6;">collision</mark> - light interacts with matter and is absorbed or scattered
	- <mark style="background: #FFB86CA6;">emission</mark> - light is emitted from matter
	- <mark style="background: #FFB86CA6;">streaming</mark> - light enters and leaves the volume we look at

### Absorption

- to model collisions with particles, we assume they are uniformly distributed in space and are rotated randomly
	- this results in a constant <mark style="background: #FFB86CA6;">density</mark> $\rho\ [1/m^3]$ and a <mark style="background: #FFB86CA6;">cross-section</mark> $\sigma\ [m^2]$ (size) that is independent of the direction 
- the <mark style="background: #FFB86CA6;">collision coefficient</mark> describes the probablility of a collision after a certain distance and is defined as 
$$\mu = \sigma \cdot \rho\ [1/m]$$
- on a macroscopic scale the coefficient is position dependent $\mu(x)$ to model heterogeneous volumes
- for absorption a collision coefficient is defined and it is assumed that the whole photon is converted into an irrelevant form of energy and thus is removed from the flux
$$-\int_\Omega\int_V \mu_a(x)L(x, \omega)dxd\omega\ [W]$$
 - from the units it can be derived that $L(x, \omega) = \frac{d\Phi}{dxd\omega}\ [W/(m^2 st)]$ (see also in [[Radiometry]])
![[Pasted image 20251106135410.png]]

### Emission

- for emission, the particles are assumed to be black body emitters
	- the absorb the whole light that hits them
	- and emit some amount of light $L_e$ then
- it also has a collision coefficient $\mu_e$ and thus the emitted light is
$$\int_\Omega\int_V \mu_e(x)L_e(x, \omega)dxd\omega\ [W]$$

### Streaming

- collect all leaving or entering photons on the boundary of the volume by projecting the direction of the light onto the normal, thus adding incoming and subtracting outgoing light (when the normal points out)
$$\int_\Omega \int_{\partial V} \langle \omega L(x,\omega), n(x) \rangle dx d\omega$$
- to not integrate over the boundary, apply the Divergence Theorem (Gauss' Theorem) 
	- so this is the change of $L$ in direction $\omega$ 
$$-\int_\Omega\int_V \frac{\partial}{\partial \omega} L(x, \omega) dxd\omega$$

## Scattering

- the <mark style="background: #FFB86CA6;">scattering kernel</mark> $k(\omega_i, x, \omega_o$ describes the probability that a photon coming from $\omega_i$ scatters in the direction of $\omega_o$ 
	- scattering is elastic, thus the wavelength stays the same
- for in-scattering, this is the gain from this
$$+\int_\Omega\int_V \int_\Omega \mathrm{k}(\omega_i,\mathbf{x},\omega) L(\mathbf{x},\omega_i)\mathrm{d}\omega_i\mathrm{d}\mathbf{x}\mathrm{d}\omega$$
- for out-scattering, this is the loss from this
$$-\int_\Omega\int_V \int_\Omega \mathrm{k}(\omega,\mathbf{x},\omega_o) L(\mathbf{x},\omega)\mathrm{d}\omega_o\mathrm{d}\mathbf{x}\mathrm{d}\omega$$
- the kernel is assumed to be separable into the scattering coefficient $\mu_s$ (the chance to hot a particle) and the phase function $f_s(\omega_o \cdot \omega_i)$ that is dependent on the cosine of the two directions
	- phase function is normalized, and thus integrates to 1
- with this, the out-scattering term can be simplified:
$$-\int_\Omega k(\omega,x,\omega_o) L(x,\omega)d\omega_o = -\mu_s(x)L(x, \omega) \int_\Omega f_s(\omega_o \cdot \omega)d\omega_o = -\mu_s(x)L(x, \omega)$$

## Building everything together

- combine losses from absorption, emission and scattering to the <mark style="background: #FFB86CA6;">extinction coefficient</mark> $\mu_t = \mu_a + \mu_e + \mu_s$
$$\begin{align}
0 = \int_\Omega\int_V  &-\overbrace{\frac{\partial}{\partial\omega} L(\mathbf{x},\omega)}^{\text{streaming}} +
\overbrace{\mu_e(\mathbf{x}) L_e(\mathbf{x},\omega)}^{\text{emission}}\, \overbrace{- \mu_t(\mathbf{x}) L(\mathbf{x},\omega)}^{\text{extinction}}\\
&+ \underbrace{\mu_s(\mathbf{x}) \int_{\Omega} f_s(\omega_i\cdot\omega) L(\mathbf{x},\omega_i)\mathrm{d}\omega_i}_{\text{in-scattering}}
\,\mathrm{d}\mathbf{x}\,\mathrm{d}\omega
\end{align}$$
- if the equation hold for every part of phase space, it also hold for individual points
$$\begin{align}\overbrace{\frac{\partial}{\partial\omega} L(\mathbf{x},\omega)}^{\text{streaming}} &=\overbrace{\mu_e(\mathbf{x}) L_e(\mathbf{x},\omega)}^{\text{emission}}\, \overbrace{- \mu_t(\mathbf{x}) L(\mathbf{x},\omega)}^{\text{extinction}}\\&+ \underbrace{\mu_s(\mathbf{x}) \int_{\Omega} f_s(\omega_i\cdot\omega) L(\mathbf{x},\omega_i)\mathrm{d}\omega_i}_{\text{in-scattering}}\end{align}$$
- this is a differential equation, which is bad for rendering

## Pure integral form

- to solve the differential, we introduce the exponential <mark style="background: #FFB86CA6;">transmittance</mark> with $d = ||x-y||$ and $\omega = (y-x)/d$
$$\begin{align}
T(\mathbf{x},\mathbf{y})    &= e^{-\tau(\mathbf{x},\mathbf{y})}\\
\tau(\mathbf{x},\mathbf{y}) &= \int_0^d\mu_t(\mathbf{x}+t\cdot\omega)\mathrm{d}t
\end{align}$$
- now integrate both sides over $\omega$ with $y = x + t\omega$ and $L_s(x, \omega) = \int_{\Omega} f_s(\omega_i\cdot\omega) L(\mathbf{x},\omega_i)$ 
$$L(\mathbf{x},\omega) = \int_0^{\infty} T(\mathbf{x},\mathbf{y}) \big(\mu_e(\mathbf{y})\cdot L_e(\mathbf{y},\omega) +\mu_s(\mathbf{y})L_s(\mathbf{y},\omega) \big)\mathrm{d}t$$
- for a boundary condition, we can impose that the classical [[Rendering Equation]] must hold on every surface of the scene, where $\mathrm{d}\omega^\perp = cos(\theta)d\omega$
$$\begin{align}
L(\mathbf{x},\omega) &= T(\mathbf{x},\mathbf{y})
   \overbrace{
   \left(
     L_e(\mathbf{y},\omega) + \int_\Omega f_r(\omega_i,\mathbf{y},\omega) L(\mathbf{y},\omega_i) \mathrm{d}\omega_i^\perp
   \right)
   }^{\text{contribution from the point }\mathbf{y} \text{ on surface}} \\
   &+ \int_0^d T(\mathbf{x},\mathbf{z})
   \underbrace{
   \left(
     \mu_e(\mathbf{z}) L_e(\mathbf{z},\omega) + \mu_s(\mathbf{z}) \int_{\Omega} f_s(\omega\cdot\omega_i)L(\mathbf{z},\omega_i)\mathrm{d}\omega_i
   \right)
   }_{\text{contribution from any point }\mathbf{z}\text{ at distance $t$ in volume}}
\mathrm{d}t
\end{align}$$ ![[Pasted image 20251107114830.png | 300]]

---

Origin: 
References: [[Radiometry]]
Tags: 
Created: 06.11.2025

