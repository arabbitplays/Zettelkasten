# Java Modelling Language (JML)

- erweitert Java um [[Design by Contract | contracts]]
```java
/*
@requires size > 0; 
@ensures size == \old(size) –1; 
@ */ 
Object pop() { …pop logic… }
```
- ![[Pasted image 20240131150404.png |400]]
```java
// \forall und \exists für Quantifizierte Anfragen
/*
@ensures (\forallinti; 0 <= i&& i< size; 
	\old(elements[i]) == elements[i]); 
@*/ 
Object pop() {…pop logic …}
```
- Definiere erlaubte Seiteneffekte definieren mit @assignable und @pure
	- Pure Methoden können in den JML Conditions verwendet werden
- Definiere erlaubte Exceptions und Handling mit @signals und @signals_only
	- Aussage hinter @signals ist die Bedingung für das Werfen, nicht der Behandlung
- Definiere Klasseninvarianten mir @invariant

---

Origin: 
References: [[Design by Contract]]
Tags: 
Created: 15.11.2024

