# Light Sources

## Introduction

- this will provide equations to describe the emitted light for different types of lights
- the Watts in the units is not the same as the Watts on light bulbs, the first is a [[Radiometry]] unit, the latter is a [[Photometry]] unit

## Types of Light
### Point Light

- a single point that emits radiant intesity into the hemisphere
$$I(\omega) = \frac{d\Phi}{d\omega}\ [W/sr]$$

### Area Light

- an area that emits radiance into the hemisphere
$$L(x, \omega) = \frac{d^2 \Phi}{dx\ cos(\theta) d\omega}\ [W/(m^2sr)]$$

### Directional Light

- emits irradiance onto infinite plane from one direction $\omega$
$$E(x) = \frac{d\Phi}{dx}\ [W/m^2]$$
- used for sunlight and [[Environment Maps]]

## Emission distribution function (EDF)

- in general models dependency on $x$ and $\omega$
- IES light profiles only model dependency on $\omega$
![[Pasted image 20251113180613.png]]
- often used: simple cosine-power emitter
$$L(\mathbf{x},\omega) = E_0(\mathbf{x}) \cdot \langle\omega,\mathbf{n}\rangle^k$$

---

Origin: 
References: 
Tags: 
Created: 13.11.2025

