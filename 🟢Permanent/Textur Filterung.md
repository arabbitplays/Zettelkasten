# Textur Filterung

## Magnification

![[Pasted image 20241128164131.png |400]]
- Abbildung weniger Texel auf viele Pixel 
- <mark style="background: #FFB86CA6;">Nearest Neighbor</mark> - Wähle die Farbe des nächstliegenden Texels (links)
- <mark style="background: #FFB86CA6;">Bilinear Interpolation</mark> - Interpoliere für den gelben Pixel aus den 4 nächsten orangenen Texeln (recht)
	- ![[Pasted image 20241128163651.png |300]]
	- Interpoliere erst horizontal dann vertikal
	- <mark style="background: #D2B3FFA6;">Die Interpolation ist nicht linear sondern quadratisch</mark>


## Minification

- Abbildung mehrerer Texel auf einen Pixel ([[Anti Aliasing]])
- Supersampling ist meist zu aufwendig
- Herausfiltern der hohen Frequenzen die das Aliasing erzeugen -> idealer weise ein perfekter Tiefpassfilter (sinc Funktion)
- In der Praxis -> [[Mipmapping]], die schlechtere Auflösung approximiert einen Tiefpassfilter

- Noch besser: <mark style="background: #FFB86CA6;">Anisotrope Filterung</mark>


---

Origin: Computergrafik
References: [[Anti Aliasing]], [[Texture Mapping]]
Tags: 
Created: 26.11.2024

