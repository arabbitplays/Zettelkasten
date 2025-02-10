# Farbräume

- Ein <mark style="background: #FFB86CA6;">Farbmodell</mark> ist das Mathematische Modell mit dem Farben durch Tupel beschrieben werden Können
- Ein <mark style="background: #FFB86CA6;">Farbraum</mark> ist die Menge alle Farben die durch die Tupel eines Modells dargestellt werden können
- <mark style="background: #FFB86CA6;">Tristimuluswerte</mark> beschreiben eine spezielle Farbe unter Angabe des Farbmodells

## RGB Farbraum

- <mark style="background: #D2B3FFA6;">Additive Farbmischung durch Addition der Spektren</mark>
- Nehme 3 Primärfarben $R, G, B$ 
	- <mark style="background: #D2B3FFA6;">Es gibt keine Spektralfarben, mit denen alle wahrnehmbare Farben darstellbar sind</mark>
- Der 3-dimensionale Farbraum ist definiert als
$$C = rR+gG+bG\ (r,g,b) \in [0,1]^3$$
## CMY Farbraum

- <mark style="background: #D2B3FFA6;">Subtraktive Farbmischung durch Multiplikation der Spektren</mark>
	- welche Bereiche werden absorbiert, welche nicht?
- Definiert über $(c,m,y) = (1,1,1) - (r,g,b)$

## HSV Farbraum

- weder additiv noch subtraktiv
- Definition über den Farbton (Hue), die Sättigung (Saturation) und Helligkeit (Value)

## Color Matching Functions

- Wie muss ich $(r,g,b)$ setzen um eine gegebene Farbe zu reproduzieren?
	- Experimentell ermittelt
![[Pasted image 20241029125651.png |300]]
- Der Bereich in dem $r$ negativ ist, ist ein Bereich an Farben, der nicht darstellbar ist
- Gegeben das Spektrum $P$ gilt (sehr ähnlich zu der Mathe in [[Human Visual System (HVS)]]):
$$r = \int \bar{r}(\lambda)P(\lambda)d\lambda \ \ \ g = \int \bar{g}(\lambda)P(\lambda)d\lambda \ \ \ b = \int \bar{b}(\lambda)P(\lambda)d\lambda$$
- Wenn $r$ negativ ist, gibt es keine [[Human Visual System (HVS)#Metamerismus |metamere]] Farbe zu $P$

## XYZ Farbraum

- Ziel ist ein standartisierter Farbraum zur Konvertierung
	- Soll alle Farben mit positiven Color Matching Funktionen darstellen können
	- Lineare Abbildung $XYZ <=> RGB$ 
- Lege die CMFs fest
	- Erzeugt physikalisch unmögliche "Primärfarben"

## xyY Farbraum

 - Trenne Chromazität und Intensität der Farbe da $(X,Y,Z)$ die selbe Chromazität hat wie $(kX, kY, kZ)$ 
- Projektion der Ebene $X+Y+Z=1$ auf die $XY$-Ebene 
$$x = \frac{X}{X+Y+Z}\ \ \ y = \frac{Y}{X+Y+Z}$$
- Implizit gibt es noch $z = \frac{Z}{X+Y+Z} = 1 - x - y$
- Helligkeit $Y$ ermöglicht Rekonstruktion mit 
$$X = \frac{Y}{y}\ \ \ Z = \frac{Y}{y}(1-x-y)$$
- Der Wertebereich von $Y$ ist bestimmt durch den <mark style="background: #FFB86CA6;">Dynamikumfang</mark> des Geräts
- Chromazitätsdiagram:
	- Die Wahl von 3 Primärfarben spannen einen <mark style="background: #FFB86CA6;">Gamut</mark> auf
		- Farben außerhalb erzeugen negative Stimuluswerte
		- Wähle stattdessen die nächste Farbe Richtung Weißpunkt
![[Pasted image 20241031163148.png | 400]]

## Psychophysisches Farbmodell

- Echt Wahrnehmung arbeitet mit Farbdifferenzen 
	- Es wird gemessen: Luminanz, Rot-Grün Differenz und Geld-Blau Differenz
- Das L\*a\*b Modell ist eine intuitive Nachbildung der Wahrnehmung
	- Euklidische Distanz entspricht wahrgenommenen Farbunterschieden

---

Origin: Computergrafik I
References: 
Tags: 
Created: 29.10.2024

