# Environment Maps

- Display of reflective objects and their mirroring without geometric representation
  - Enables faking of reflections without [[Raytracing]]
  - Save an image of the environment in a [[Texture Mapping#Sphere Mapping | Sphere Map]] or a cube map

- For imperfect reflections: Light around the reflection direction contributes the most
  - Pre-filtering of the texture possible to save later calculation
	  - for specular reflections, the reflection vector is used to index the environment map, else its the normal
  - Size and weighting of the texture depends on the [[Bidirectional Reflectance Distribution Function (BRDF) |BRDF]]

---

Origin: Computergrafik
References: 
Tags: 
Created: 07.12.2024
