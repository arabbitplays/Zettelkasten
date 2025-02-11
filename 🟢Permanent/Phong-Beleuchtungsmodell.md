# Phong-Beleuchtungsmodell

- Besteht aus 3 Komponenten
	- Ambient - indirekte Beleuchtung aus der Umgebung
	- Diffuse
	- Specular - imperfekte Spiegelung
- Diffuse und Specular sind nur vorhanden, wenn das Objekt nicht im Schatten liegt
- $n$ ist Normale, $l$ Vektor Richtung Licht, $x$ ist die Position, $v$ Vektor Richtung Kamera, alle normalisiert
- $L$ ist die Lichtstärke aus Richtung $l$
## Diffuse

- ideal diffuse Reflektion, also gleichmäßig in alle Richtungen
- Wenn der Strahl von vorne kommt ($|\theta| < \pi / 2)$ gilt für die Bestrahlung der Fläche
$$I_L \propto cos(\theta) = n \cdot l$$
- Nutze diffuse Farbe $k_d$ 
$$L\ k_d\ max(0, n \cdot l)$$

## Specular 

- Glanzlicht liegt in der idealen Reflexionsrichtung
$$r_l = 2(l \cdot n)n -l$$
- Stärke fällt weiterentfernt von $r_l$ ab, modelliert durch
$$L\ k_s\ max(ß, r \cdot v)^n$$
- Ein großen $n$ erzeugt kleinere Glanzlichter

## Ambient

- Nur modelliert über einen Parameter $k_a$ und es gilt
$$k_a\ L$$

---

Origin: Computergrafik
References: [[Remote Zettelkasten/🟢Permanent/Raytracing|Raytracing]]
Tags: #🇩🇪 
Created: 12.11.2024

