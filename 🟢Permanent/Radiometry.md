# Radiometry


- For rendering, operate on <mark style="background: #FFB86CA6;">geometric optics</mark> levels
	- macroscopic properties of light suffice to describe the interaction with large objects relative to the wavelength
	- leads to some central assumptions
		- linearity: contributions of two inputs into a system equals the contribution of the sum of the inputs
		- energy conservations: scattering events don't produce energy
		- no polarization: humans can not perceive the polarization of light, so it is assumed to be unpolarized
		- steady state: the radiance distribution is not changing over time, the light has always reached equilibrium

- <mark style="background: #FFB86CA6;">Speed</mark> $c_m$ is dependend on the index of refraction $\mu_m$ of the medium ($c = c_m \mu_m$)
- <mark style="background: #FFB86CA6;">Wavelength</mark> $\lambda_m\ [nm]$ or <mark style="background: #FFB86CA6;">frequency</mark> $f = c_m / \lambda_m$ (dependent on $\mu_m$)
- <mark style="background: #FFB86CA6;">Energy of a photon</mark> $q = hf\ [J]$ (Planck’s constant $h$)
	- Multiplied with the photon count $P$ gets the energy of a light source $Q = P hf$
- <mark style="background: #FFB86CA6;">Radiant flux</mark> is the energy of a light source over time $\Phi = dQ / dt\ [W = Js^-1]$
- <mark style="background: #FFB86CA6;">Irradiance</mark> is how much flux gets to a surface from any direction
	- $$E = \frac{d\Phi}{dA}\ [W/m^2]$$
	- <mark style="background: #FFB86CA6;">Radiant exitance</mark> is an alternate term for the flux leaving a surface
	- From this quantity [[Lambert's law]] is derivable
- <mark style="background: #FFB86CA6;">Radiosity</mark> is how much light leaves a point per unit area 
	- $$B(x) = \frac{d\Phi}{dA} [W/m^2]$$
- <mark style="background: #FFB86CA6;">Radiance</mark> is how much light arrives at a surface from a give direction ([[Solid Angle]] $\omega$) 
	- $$L = \frac{dE}{d\omega} = \frac{dE}{dA^\Phi d\omega} [W/m^2 sr]$$

	- $A^\Phi$ is the area projected kn the plane perpendicular to $\omega$ ($dA^\Phi = dA\ cos(\Phi)$)
	- ![[Pasted image 20241119121536.png |200]]
	- <mark style="background: #D2B3FFA6;">Radiance is constant along a ray in free space</mark>


| Incoming | Outgoing                                                                  |
| -------- | ------------------------------------------------------------------------- |
| data     | path to data files to supply the data that will be passed into templates. |
| engine   | engine to be used for processing templates. Handlebars is the default.    |
| ext      | extension to be used for dest files.                                      |
|          |                                                                           |



- Relationship between radiance and irradiance 
$$E(x) = \int_{\Omega^+}L(x, \omega)cos(\Phi)d\omega$$

- Light consists of multiple wavelengths $P(\lambda)$
	- Perception of this distribution depends on the [[Human Visual System (HVS)]]
	- Reflection, transmission and emission are all wavelength dependent 

---

Origin: Computergrafik I
References: [[The Physics of Shading]]
Tags: 
Created: 29.10.2024

