# Räumliche Datenstrukturen

- Beschleunige Ray Traversierung durch die Verringerung von Ray-Triangle Schnitttests

## Typen
- [[Bounding Volume Hierarchie (BVH)]]
-  [[Binary Space Partitioning Tree (BSP)]]
- Reguläre Gitter
	- Einteilung des Raumes in Zellen gleicher Größe und Form
	- Eintragen der Objekte in Zellen die von ihm geschnitten wurde
	- Traversierung der vom Strahl geschnittenen Zellen, Schnitttest mit den enthaltenen Objekten
	- <mark style="background: #D2B3FFA6;">Adaptive Unterteilung des Gitters</mark>
		- ![[Pasted image 20241217132504.png |300]]

## Konstruktion

- Beginne mit einer riesigen bounding box und unterteile diese rekursiv in neue Boxen (bei BVHs) oder in zwei Seiten (bei kD-Bäumen)
	- Wahl der Schnitte beeinfluss spätere Performance
- Ziel:
	- Finde kompakte und dicht besiedelte Regionen
	- Abtrennen von dünn besetzten Regionen -> später dann sehr kleine Hüllkörper

### Räumliches Mittel

- teilen entlang der Achse der größten Ausdehnung
- <mark style="background: #FF5582A6;">Oftmals sehr unbalanciert</mark>
- $O(n\ log(n)$
### Objektmittel

- teile so, dass beide Kinderknoten gleich viele Primitive haben
- $O(n\ log^2(n))$
### Surface Area Heuristik

$$C=C_T + P(treffe\ L)C(L) + P(treffe\ R)C(R)$$
- $C_T$ sind die Kosten für die Entscheidung, mit welchem Kindknoten fortgefahren wird
- $P$ ist die Wahrscheinlichkeit, dass der linke/rechte Kindknoten getroffen wird
	- Sei $SA(B)$ die Surface Area einer Box, dann gilt $P(treffe\ X) = \frac{SA(B_X)}{SA(B_P)}$
- $C(L), C(R)$ sind die Kosten für die Traversierung des linken/rechten Kindknotens
	- meistens $Primitivkosten \times Anzahl$ 
- $O(n\ log^2(n))$
---

Origin: 
References: [[Zettelkasten/🟢Permanent/Raytracing|Raytracing]]
Tags: 
Created: 17.12.2024

