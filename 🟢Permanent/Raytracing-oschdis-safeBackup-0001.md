# Raytracing

- Grundlegende Schritte:
	- Ray Generation - Erzeugung von Strahlen pro Pixel
	- Ray Casting / Intersection - Finde das erste getroffene Dreieck
	- Shading - Schattierung und Beleuchtungsberechnung
	- Sekundärstrahlen - Für Spiegelung oder Transmission weitere Strahlen erzeugen

## Ray Generation

![[Pasted image 20241105121929.png | 300]]
- Definiere einen normalisierten "Up-Vektor"
- $w$ ist negative Blickrichtung
- $u = up \times w$ und $v = w \times u$
- $d$ ist Abstand von $e$ zur Bildebene
- Gegeben eines Punktes $(u, v)$ der Bildebene ist der Strahl:
$$s = u \textbf{u} + v \textbf{v} - d\textbf{w},\ r(t) = e + t \frac{s}{|s|} = e+td$$
- Durch [[Anti Aliasing]] teils sub pixel Abstände

## Ray Intersection

- Hier genauer: Strahl-Dreieck Intersection
- Nutzt [[Baryzentrische Koordinaten]] indem die Vektoren $e_1 = P_2-P_1$ und $e_2 = P_3-P_1$ eine Ebene aufspannen
$$e+td = P_1 + \lambda_2 e_1 + \lambda_3 e_2$$
- Schnittpunkt mit dem Dreieck wenn $\lambda_2, \lambda_3 \geq 0 \wedge \lambda_2 + \lambda_3 < 1$
- Schnittpunkt in Richtung des Strahls wenn $t > 0$
- Dieses Gleichungssystem kann mit der Cramerschen Regel gelöst werden

## Shading 

- Siehe [[The Physics of Shading]]
- Also Normale wird entweder die Dreiecksnormale genutzt <mark style="background: #FFB86CA6;">(Flat Shading)</mark> oder interpoliert über die Vertex Normalen <mark style="background: #FFB86CA6;">(Phong Shading)</mark>

## Verschiedene Raytracing Varianten

- [[Whitted Style Raytracing]]
- [[Distributed Raytracing]]
- [[Path Tracing]]

---

Origin: Computergrafik I
References: 
Tags: 
Created: 05.11.2024

