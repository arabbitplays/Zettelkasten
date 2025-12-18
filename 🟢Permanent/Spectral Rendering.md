# Spectral Rendering

## Introduction

- instead of calculating all quantities as RGB values, we represent color as a wavelength dependent spectrum $S(\lambda) \in \mathbb{R}_{\geq 0}$ 
- this allows for more accurate color representation and wavelength dependent effects like dispersion
- it introduces color noise because the spectrum is sampled on random wavelength, that get assigned to a path 
- normally this is only done for the visible spectrum $\lambda \in \Lambda = [360nm, 830nm]$ 

## Spectrum to RGB

- this is needed to display the spectrum on the screen
- the spectrum is first transformed into the [[Color Spaces#XYZ color space]] with the CIE XYZ color matching functions (same formula with $\bar{y}$ and $\bar{z}$)
$$X = \frac{1}{N}\int_\Lambda \bar{x}(\lambda)S(\lambda)I(\lambda)d\lambda$$
- where $I$ is the spectral power distribution of the reference illuminant (D65 for standard RGB) and $N = \int_\Lambda \bar{y}(\lambda)I(\lambda)d\lambda$ 
- and then the XYZ triple is transformed into a RGB triple via the transformation matrix

## RGB to spectrum

- this is needed for loading environment maps, light emission and reflection spectra
- the simplest technique uses spectra for the three linear RGB colors: $S_r(\lambda), \dots$ 
- and then the result is calculated as a linear combination 
$$S(\lambda) = r S_r(\lambda) + gS_g(\lambda) + bS_b(\lambda)$$

## Spectral tracing

- now for each path, four wavelengths can be sampled and the result calculated
- when $\omega_i$ depends on the wavelength, only the path of the first (<mark style="background: #FFB86CA6;">hero</mark>) wavelength is traced (but the contribution is calculated for all 4)
- the results are better, when the wavelengths are stratified by rolling only one $\xi \in [0,1)$ and using $(\xi + i * 0.25) \% 1$ for the i-th wavelength

---

Origin: 
References: 
Tags: 
Created: 27.11.2025

