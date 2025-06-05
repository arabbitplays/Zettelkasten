# Shadow Maps

## Introduction

A realtime rendering technique where a depth buffer is rendered from the view of the light source and used to determine, if a point seen from the camera is shadowed or not.

## Base Idea

- view the light source as a perspective camera, then every texel corresponds to a direction in space
	- the texture saves to distance to the closest surface point
- for a point $y$ seen from the camera
	- calculate the distance to the camera $l$
	- the direction from the light to $y$ maps to a texture coordinate in the shadow map
	- look up closest distance $d$ from the shadow map
	- is $d=l$ the point is not shadowed, if $d>l$ then the point is shadowed
- generate one shadow map for every light source

## Problems

### Shadow Acne

- the shadow map is a discrete sampling of the geometry, and the distance is only recorded at the center of a texel
![[Pasted image 20250515142409.png]]
- solution: move the surface a bit away from the light source by adding a little extra distance to the value recorded in the shadow map
	- is this offset is to big, parts of the shadow can go missing

### Aliasing

- because the resolution of the shadow map is finite, the texel of the map can become visible at the border of a shadow
![[Pasted image 20250515142725.png]]
- important factor is how much area in the scene corresponds to a texel in the shadow map compared to a texel in the final image
![[Pasted image 20250515143226.png | 150]]
- given the size of a texel in the shadow map $d_s$, the distance of the point to the light $r_s$ and the angle to the surface normal $\alpha_s$, the area $A$ covered by the texel is
$$A \approx r_s * d_s / cos(\alpha_s)$$
- the same can be done for the camera ($A \approx r_i * d_i / cos(\alpha_i)$) and so the size of $A$ in the final image is $$d_i = d_s\frac{r_s * cos(\alpha_i)}{r_i * cos(\alpha_s)}$$
- ideal would be $d_i = d_s$ 

## Shadow Map Sampling

- to decrease aliasing artefacts, sample geometry finer close to the camera

### Perspective Shadow Maps (PSM)

- reduce aliasing artefacts by first applying the perspective transformation of the camera to the scene, before rendering the shadow map
- the properties of the perspective transformation requires a special case handling when doing the depth comparison
	- if the light is behind the camera, the depth test has to be inverted

### Trapezoidal Shadow Maps (TSM)

- even better sampling close to the camera, see [here](http://diglib.eg.org/items/35e36c54-e42c-435b-a9b7-b99cee2035b4 )

### Cascading Shadow Maps 

- PSM and TSM can be hard to handle through special cases
- more practical relevant are cascading shadow maps
	- view frustum of the camera is split into cascades
	- every cascade gets its own shadow map with the same resolution
	- choose the best cascade and interpolate between to in overlapping areas
- <mark style="background: #BBFABBA6;">easy to use</mark>
- <mark style="background: #FF5582A6;">makes shadow map calculation more expensive</mark>

## Filtering

- normal shadow maps only provide hard shadows
	- blur them to achieve soft shadows
- classic [[Texture filtering]] does not work on the depth values of the shadow map 
- use <mark style="background: #FFB86CA6;">Percentage Closer Filtering (PCF)</mark> 
	- shadow test is done with the four neigboring texels, results are interpolated
	- doesn't remove aliasing, only blurring the seen texel
	- or needing a very big kernel (using a bigger neighborhood) making the filtering very expensive very quickly

### Variance Shadow Mapping

- store not only depth (in the red channel) but also the depth squared in the green channel
	- filter them like above $R = \sum w_i z_i$, $G = \sum w_i z_i^2$
- deduce the mean and the variance of the depth distribution $\mu = R, \sigma^2 = G - R^2$
- calculate the "chance" that the point is shaded given these two value (Cantellis Inequation)
- <mark style="background: #BBFABBA6;">much better edges</mark>
- <mark style="background: #FF5582A6;">light leaking: unshadowed edges behind small geometry</mark>
	- Cantelli underestimates the shadow probability -> no shadows where they should be
	- solution -> <mark style="background: #FFB86CA6;">Moments Shadow Mapping</mark> using 4 channels
		- reconstruction gets very complicated



---

Origin: 
References: 
Tags: 
Created: 15.05.2025

