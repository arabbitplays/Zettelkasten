# Bounding Volume Hierarchie (BVH)


- <mark style="background: #FFB86CA6;">Axis Aligned Bounding Box (AABB)</mark> fasst mehrere Primitive zusammen
	- Test gegen die Box, erst dann gegen die Primitive in der Box
	- Hierarchie indem die Boxen auch in Boxen kommen
- Teste zuerst die Wurzelbox und bei einem Treffer die Kinderboxen
	- Nähere Boxen zuerst, auch wenn es sein kann, dass kein Primitiv getroffen wurde
	- Nicht direkter Abbruch, da durch Überlappung der Boxen eine hintere Box den clostest hit generiert
- Reduziert $O(n)$ Schnitttests zu $O(log(n))$ Tests
- Schnelle Konstruktion in $O(nlog(n))$
- Optimale Konstruktion in $O(nlog^2(n))$  

---

Origin: Computergrafik
References: [[Räumliche Datenstrukturen]]
Tags: 
Created: 13.12.2024

