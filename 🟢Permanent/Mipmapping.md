# Mipmapping

- Methode der [[Texture filtering]] für [[Anti Aliasing]]
- Speichere mehrere Auflösungsstufen der Textur -> benötigt nur $1/3$ mehr Speicherplatz
	- ![[Pasted image 20241129144259.png |200]]
- Wähle abhängig von der Entfernung zur Kamera
	- <mark style="background: #FFB86CA6;">Trilineare Interpolation</mark> - Berechne das Ergebnis auf 2 Mipmap Stufen und Interpoliere dazwischen -> Versteckt die Übergänge ein wenig

- <mark style="background: #FF5582A6;">Problem: Aliasing könnte nur auf einer Achse stattfinden, dadurch unnötiger Qualitätsverlust in der anderen Achse</mark>

---

Origin: Computergrafik I
References: [[Texture filtering]]
Tags: 
Created: 28.11.2024

