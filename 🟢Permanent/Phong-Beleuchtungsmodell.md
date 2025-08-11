# Phong lighting model

- Consists of 3 components
- Ambient - indirect lighting from the surroundings
- Diffuse
- Specular - imperfect reflection
- Diffuse and specular are only present if the object is not in shadow
- $n$ is normal, $l$ vector towards light, $x$ is the position, $v$ vector towards camera, all normalized
- $L$ is the light intensity from direction $l$
## Diffuse

- ideally diffuse reflection, i.e. evenly in all directions
- If the beam comes from the front ($|\theta| < \pi / 2)$, the following applies to the irradiation of the surface
$$I_L \propto cos(\theta) = n \cdot l$$
- Use diffuse color $k_d$ 
$$L\ k_d\ max(0, n \cdot l)$$

## Specular 

- Specular highlight lies in the ideal reflection direction
$$r_l = 2(l \cdot n)n -l$$
- Strength falls off further away from $r_l$, modeled by
$$L\ k_s\ max(ß, r \cdot v)^n$$
- A large $n$ produces smaller highlights

## Ambient

- Only modeled via a parameter $k_a$ and the following applies
$$k_a\ L$$
---

Origin: Computergrafik
References: [[Zettelkasten/🟢Permanent/Raytracing|Raytracing]]
Tags:  
Created: 12.11.2024

