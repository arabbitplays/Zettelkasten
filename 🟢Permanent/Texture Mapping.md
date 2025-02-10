# Texture Mapping

## Anwendungen

- Color Mapping (Diffuse Parameter im [[Phong-Beleuchtungsmodell]])
- Gloss Mapping (Specular Parameter im [[Phong-Beleuchtungsmodell]])
- Normal Mapping -> nutze die Normale in der Textur
	- Bump Mapping -> rotiere die Normale entsprechend der Textur
- Displacement Mapping -> verschiebe die Positionen der Vertices entsprechend der Textur
- Ambient Occlusion

## Natürliche Parametrisierung

- Die uv-Koordinaten einer Ebene sind trivial
- Eine Kugel ist durch die Kugelkoordinaten $(r, \phi, \theta)$ mit $(u,v)=(\phi/2\pi, \theta/2\pi)$
- Ein Zyliner ist durch Zylinderkoordinaten $(r, \phi, \gamma)$ mit $(u,v) = (\phi/2\pi, \gamma/h)$ 
- Würfel sind durch 6 Ebenen Parametrisierbar

## Beliebige Parametrisierung

- Abbilden der Textur auf einen Standardkörper und dann auf das eigentliche Objekt
![[Pasted image 20241126132010.png | 400]]
![[Pasted image 20241126132218.png |400]]

## Explizite Parametrisierung

- Bei Dreiecksnetzen werden uv-Koordinaten pro Vertex explizit gespeichert 
	- Interpolation mit [[Baryzentrische Koordinaten]]
- Werden oft auch (Semi-)manuell festgelegt

## Sphere Mapping

- Fotografieren einer reflektierenden Kugel von vorne
- Bild der Kugel wird eine sogenannte Sphere Map
![[Pasted image 20241207124752.png | 400]]
## Texture Wrapping


- Definiert wie mit Texturkoordinaten $(u,v) \notin [0,1]^2$ umgegangen wird
	- <mark style="background: #FFB86CA6;">Clamp-Mode</mark> - Gibt einen Standardwert zurück
	- <mark style="background: #FFB86CA6;">Repeat-Mode</mark> - Wiederholt die Textur immer wieder
	- Kann für jede Achse einzeln definiert werden
![[Pasted image 20241126133103.png | 400]]

## [[Textur Filterung]]


---

Origin: Computergrafik I
References: [[Rendering Index]]
Tags: 
Created: 26.11.2024

