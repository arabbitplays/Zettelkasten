# Whitted Style Raytracing

- model all lights a single points
	- the light can be sampled with a single ray directly to the light source
- generate new ray into the perfect reflection direction (Reflection-Rays) and into the perfekt transmission direction according to [[Snells Law of Refraction]]
	- weigh both results with the fresnek value
![[Pasted image 20241114155454.png |400]]

- <mark style="background: #FF5582A6;">Only hard shadows and perfect reflektions</mark>

---

Origin: Computergrafik I
References: [[Zettelkasten/🟢Permanent/Raytracing|Raytracing]]
Tags: 
Created: 19.11.2024

