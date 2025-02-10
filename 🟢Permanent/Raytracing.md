# Raytracing

- Basic Steps:
	- Ray Generation - Generation one or multiple sample rays (<mark style="background: #FFB86CA6;">primary rays</mark>) per pixel
	- Ray Casting / Intersection - find the first or all primitives that intersect the ray
	- Shading - calculate lighting at the intersection
	- Sekundärstrahlen - generate secondary rays for reflection and transmission

## Ray Generation

![[Pasted image 20241105121929.png | 300]]
- define normalized "Up-Vektor"
- $w$ is negative view direction 
- $u = up \times w$ and $v = w \times u$
- $d$ is distance from $e$ to the image plane
- given a point $(u, v)$ of the image plane generate the ray
$$s = u \textbf{u} + v \textbf{v} - d\textbf{w},\ r(t) = e + t \frac{s}{|s|} = e+td$$

- use sub pixel distance for [[Anti Aliasing]] 

## Ray Intersection

- hear: Ray-Triangle Intersection 
- use [[Baryzentrische Koordinaten]] where the vectors $e_1 = P_2-P_1$ and $e_2 = P_3-P_1$ define a plane
$$e+td = P_1 + \lambda_2 e_1 + \lambda_3 e_2$$
- Intersection with the triangle when $\lambda_2, \lambda_3 \geq 0 \wedge \lambda_2 + \lambda_3 < 1$
- Intersection is in the right direction of the ray if $t > 0$
- solve equation system wirth Cramers Rule

## Shading 

- see [[💡Resources/📦Zettelkasten/🟢Permanent/Raytracing|Raytracing]]
- as a normal use triangle normal <mark style="background: #FFB86CA6;">(Flat Shading)</mark> or the interpolated vertex normals <mark style="background: #FFB86CA6;">(Phong Shading)</mark> (see [[Normal Transformations]])

## Different Raytracing Variants

- [[Whitted Style Raytracing]]
- [[Distributed Raytracing]]
- [[Path Tracing]]

---

Origin: Computergrafik I
References: 
Tags: 
Created: 05.11.2024

