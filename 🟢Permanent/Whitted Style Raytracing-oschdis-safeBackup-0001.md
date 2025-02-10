# Whitted Style Raytracing

- Modelliere alle Lichtquellen als Punkte
	- Ermöglicht einen Schattenstrahl, der testet ob der Punkt die Lichtquelle sieht
- generiere weitere Strahlen in Richtung der perfekten Reflektion (Reflektionsstrahl) und in Richtung der Transmission (abhängig von [[Snellsches Brechungsgesetz]])
	- gewichte beide Ergebnisse durch den Fresnel Term
![[Pasted image 20241114155454.png |400]]

- <mark style="background: #FF5582A6;">Nur harte Schatten und perfekte Spiegelungen</mark>

---

Origin: Computergrafik I
References: [[💡Resources/📦Zettelkasten/🟢Permanent/Raytracing]]
Tags: 
Created: 19.11.2024

