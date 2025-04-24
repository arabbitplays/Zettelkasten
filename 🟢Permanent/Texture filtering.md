# Texture filtering

## Magnification

![[Pasted image 20241128164131.png |400]]
- Map fewer texels to many pixels 
- <mark style="background: #FFB86CA6;">Nearest Neighbor</mark> - Select the color of the nearest texel (left)
- <mark style="background: #FFB86CA6;">Bilinear Interpolation</mark> - Interpolate for the yellow pixel from the 4 nearest orange texels (right)
- ![[Pasted image 20241128163651.png |300]]
	- Interpolate first horizontally then vertically
- <mark style="background: #D2B3FFA6;">The interpolation is not linear but quadratic</mark>


## Minification

- Mapping of several texels to one pixel ([[Anti Aliasing]])
- Supersampling is usually too complex
- Filtering out the high frequencies that generate the aliasing -> ideally a perfect low-pass filter (sinc function)
- In practice -> [[Mipmapping]], the poorer resolution approximates a low-pass filter

- Even better: <mark style="background: #FFB86CA6;">Anisotropic filtering</mark>

---

Origin: Computergrafik
References: [[Anti Aliasing]], [[Texture Mapping]]
Tags: #🇩🇪
Created: 26.11.2024

