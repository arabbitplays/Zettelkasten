# Color Spaces

- A <mark style="background: #FFB86CA6;">color model</mark> is the mathematical model with which colors can be described by tuples
- A <mark style="background: #FFB86CA6;">color space</mark> is the set of all colors that can be represented by the tuples of a model
- <mark style="background: #FFB86CA6;">Tristimulus values</mark> describe a specific color by specifying the color model

## RGB color space

- <mark style="background: #D2B3FFA6;">Additive color mixing by adding the spectra</mark>
- Take 3 primary colors $R, G, B$ 
- <mark style="background: #D2B3FFA6;">There are no spectral colors with which all perceptible colors can be represented</mark>
- The 3-dimensional color space is defined as
$$C = rR+gG+bG\ (r,g,b) \in [0,1]^3$$
## CMY color space

- <mark style="background: #D2B3FFA6;">Subtractive color mixing by multiplying the spectra</mark>
- Which areas are absorbed, which are not?
- Defined via $(c,m,y) = (1,1,1) - (r,g,b)$

## HSV color space

- neither additive nor subtractive
- Definition via hue (Hue), saturation (Saturation) and brightness (Value)

## Color Matching Functions

- How do I have to set $(r,g,b)$ to reproduce a given color?
	- Determined experimentally
![[Pasted image 20241029125651.png |300]]
- The range in which $r$ is negative is a range of colors that cannot be represented
- Given the spectrum $P$ (very similar to the math in [[Human Visual System (HVS)]]):
$$r = \int \bar{r}(\lambda)P(\lambda)d\lambda \ \ \ g = \int \bar{g}(\lambda)P(\lambda)d\lambda \ \ \ \ b = \int \bar{b}(\lambda)P(\lambda)d\lambda$$
- If $r$ is negative, there is no [[Human Visual System (HVS)#metamerism |metamers]] Color to $P$

## XYZ color space

- The goal is a standardized color space for conversion
- Should be able to display all colors with positive color matching functions
- Linear mapping $XYZ <=> RGB$ 
- Define the CMFs
- Creates physically impossible "primary colors"

## xyY color space

 - Separate chroma and intensity of the color since $(X,Y, Z)$ has the same chromacity as $(kX, kY, kZ)$ 
- Projection of the plane $X+Y+Z=1$ onto the $XY$ plane 
$$x = \frac{X}{X+Y+Z}\ \ \ y = \frac{Y}{X+Y+Z}$$
- Implicitly there is still $z = \frac{Z}{X+Y+Z} = 1 - x - y$
- Brightness $Y$ allows reconstruction with 
$$X = \frac{Y}{y}\ \ \ Z = \frac{Y}{y}(1-x-y)$$
- The value range of $Y$ is determined by the <mark style="background: #FFB86CA6;">dynamic range</mark> of the device
- Chromaticity diagram:
- The choice of 3 primary colors spans a <mark style="background: #FFB86CA6;">gamut</mark> on
- Colors outside generate negative stimulus values
- Choose the next color towards the white point instead
![[Pasted image 20241031163148.png | 400]]

## Psychophysical color model

- Real perception works with color differences 
- It is measured: Luminance, red-green difference and money-blue difference
- The L\*a\*b model is an intuitive reproduction of perception
- Euclidean distance corresponds to perceived color differences -> <mark style="background: #FFB86CA6;">perceptual uniform</mark> 
- other uniform color spaces:
	- The Munsell System
		- the three dimensions are hue, chroma and value
		- created through thousands of observations and experiments with the HVS
			- thus still an approximation, but a good one
	- CIE Lab
	- [OkLab](https://bottosson.github.io/posts/oklab/)

---

Origin: Computergrafik I
References: 
Tags: 
Created: 29.10.2024

