# The Physics of Shading

There are two main ways of light interacting with surfaces
- <mark style="background: #FFB86CA6;">Absorption</mark> - The direction stays the same, but the intensity of different wavelengths change
- <mark style="background: #FFB86CA6;">Scattering</mark> - Doesn't change the intensity of light, but splits it in multiple directions
	- Happens in heterogeneous media where the index of refraction changes very abruptly
	- Has only an analytical solution on a perfectly planar boundary
		- Light is <mark style="background: #FFB86CA6;">reflected</mark> (away from the surface) and <mark style="background: #FFB86CA6;">refracted</mark> (into the surface)

- In metals, refracted light is directly absorbed
- In dielectrics refracted light is scattered so much that it is remitted at varying points from the surface -> <mark style="background: #FFB86CA6;">subsurface scattering</mark>
	- If the distance between entry and exit is smaller than pixel on the screen, the emitted light only depends on the entering light
	- Else, subsurface scattering has to be specifically modeled

---

Origin: Background: Physics and Math of Shading - by Naty Hoffman
References: [[Vulkan Index]]
Tags: 
Created: 28.09.2024

