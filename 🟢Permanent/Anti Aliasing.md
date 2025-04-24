# Anti Aliasing

- <mark style="background: #FFB86CA6;">Aliasing</mark> sind Artefakte durch die Verletzung des [[Shannon-Abtasttheorem]]
- typische Quellen von Aliasing 
	- detaillierte Geometrie 
	- Texturen/Textursignale (Farben, Normalen, ...)
	- Shading (z.B. Glanzlichter auf gekrümmten Flächen)

## Texturen

- Vorfiltern -> hohe Frequenzen entfernen ([[Texture filtering]])
## Supersampling

- Mehrfach samplen und dann mitteln
- <mark style="background: #FFB86CA6;">Uniformes Supersampling</mark>
	- ![[Pasted image 20241116091744.png |300]]
	- Kann dennoch Artefakte erzeugen
- Stochastisches Supersampling bzw <mark style="background: #FFB86CA6;">Stratified Supersampling</mark>
	- ![[Pasted image 20241116091903.png |200]]
	- Zufällige Position im Teilbereich des Pixels
	- Reduziert aliasing aber führt zu Rauschen -> dennoch besser
- <mark style="background: #FFB86CA6;">Blue Noise Sampling</mark>
	- Vorberechnete zufällige Punkte mit uniformen Abstand
	- ![[Pasted image 20241116092106.png |200]]
	- Unerlässlich, vor allem bei Realtime [[💡Resources/📦Zettelkasten/🟢Permanent/Raytracing]]

---

Origin: 
References: 
Tags: 
Created: 16.11.2024

