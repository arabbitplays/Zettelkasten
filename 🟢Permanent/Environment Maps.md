# Environment Maps

- Darstellung reflektierender Objekte und deren Spiegelung ohne geometrische Repräsentation
  - Ermöglicht faken von Reflektionen ohne Reytracing
  - Speichere ein Bild der Umgebung in einer [[Texture Mapping#Sphere Mapping | Sphere Map]] oder einer Cube Map

- Für imperfekte Spiegelungen: Licht um die Reflektionsrichtung herum trägt am meisten bei
  - vorfiltern der Textur möglich um spätere Berechnung zu sparen
  - Größe und Gewichtung der Textur abhängig von der [[Bidirectional Reflectance Distribution Function (BRDF) |BRDF]]

---

Origin: Computergrafik
References: 
Tags: 
Created: 07.12.2024
