# Gamma Korrektur


## Transferfunktionen

- Mappt die Werte aus dem Framebuffer (Pixelwerte $p$) auf die möglichen Helligkeitswerte des Bildschirms
- Meist eigene Transferfunktion pro Farbkanal
- Anhängig von gewünschten Darstellungscharakteristika
- Abhängig von physikalischen Eigenschaften des Bildschirms
	- Eingeschränkt durch die maximale und minimale Helligkeit des Displays
	- Und vom Bildschirm reflektiertes Umgebungslicht $k$
- <mark style="background: #FFB86CA6;">Dynamikumfang</mark> gibt den möglichen Kontrast an
$$R_d = \frac{I_{max} + k}{I_{min} + k}$$

## Transferfunktionen und Perzeption

Wie sieht die Ideale Transferfunktion aus?

Farben sollen keine sichtbaren Helligkeitsstufen erzeugen
- Menschen nehmen nur einen Helligkeitsunterschied von 1-2% war (<mark style="background: #FFB86CA6;">Just noticable difference (JND)</mark>)
	- Abhängig von der Hintergrundhelligkeit $L$, <mark style="background: #D2B3FFA6;">absolut kleinere Schritte im dunklen</mark>
$$\frac{L_{LND}}{L} = const = 1\%$$
Für eine ideale Transferfunktion sollte also gelten:
$$p \mapsto 1,02^{p-1}\ I_{min}$$
$$I(p) \propto p^\gamma$$
Durch das Zusammenspiel von Bildschirm, Software, GPU usw. ist Gamma nicht all zu leicht zu bestimmen
## Gammakorrektur

Für Speicherung und Darstellung ist $I \propto p^\gamma$ ideal, da die Bits entsprechend der Perception ausgenutzt werden.
Bei der Berechnung von Bildern sollte allerdings in Linear Space stattfinden (Summe zweier Lichtquellen sollte das Doppelte sein).
Also sollte für die berechnete helligkeit $a$ gelten: $I \propto a$.
Für lineares Verhalten bei der Ausgabe: Gammakorrektur $p \propto a^{1/\gamma}$

- Ziel: $I(p) \propto a$
- Dafür setze $p = a^{1/\gamma}$

Bilder werden mit potenzbasierter Quantisierung gespeichert (unter Angabe des Exponenten). Für korrekte Darstellung muss Quantisierung invertiert werden und abschließende Gammakorrektur für das aktuelle Display System.

---

Origin: Computergrafik I
References: 
Tags: #🇩🇪 
Created: 24.10.2024

