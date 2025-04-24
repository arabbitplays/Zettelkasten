# Texture Mapping

## Applications

- Color Mapping (diffuse parameters in the [[Phong lighting model]])
- Gloss Mapping (specular parameters in the [[Phong lighting model]])
- Normal Mapping -> use the normals in the texture
- Bump Mapping -> rotate the normals according to the texture
- Displacement Mapping -> move the positions of the vertices according to the texture
- Ambient Occlusion

## Natural parameterization

- The uv-coordinates of a plane are trivial
- A sphere is defined by the sphere coordinates $(r, \phi, \theta)$ with $(u,v)=(\phi/2\pi, \theta/2\pi)$
- A cylinder can be parameterized by cylinder coordinates $(r, \phi, \gamma)$ with $(u,v) = (\phi/2\pi, \gamma/h)$ 
- Cubes can be parameterized by 6 planes

## Arbitrary parameterization

- Mapping the texture to a standard body and then to the actual object
![[Pasted image 20241126132010.png | 400]]
![[Pasted image 20241126132218.png |400]]

## Explicit parameterization

- For triangle meshes, uv coordinates are stored explicitly for each vertex 
- Interpolation with [[barycentric coordinates]]
- Are often also defined (semi-)manually

## Sphere Mapping

- Photographing a reflecting sphere from the front
- Image of the sphere becomes a so-called sphere map
![[Pasted image 20241207124752.png | 400]]
## Texture Wrapping


- Defines how texture coordinates $(u,v) \notin [0,1]^2$ are handled
- <mark style="background: #FFB86CA6;">Clamp-Mode</mark> - Returns a default value
- <mark style="background: #FFB86CA6;">Repeat-Mode</mark> - Repeats the texture again and again
- Can be defined individually for each axis
![[Pasted image 20241126133103.png | 400]]

## [[Texture filtering]]


---

Origin: Computergrafik I
References: [[Rendering Index]]
Tags: 
Created: 26.11.2024

