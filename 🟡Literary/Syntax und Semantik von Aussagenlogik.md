# Syntax und Semantik von Aussagenlogik

## Syntax

- Logische Zeichen
	- 1, 0, Negation, Konjunktion, Disjunktion, Implikation, Äquivalenz und die Klammern
- <mark style="background: #FFB86CA6;">Signatur</mark>
	- Ein abzählbare Menge $\Sigma$ an Symbolen 
- Definiere Menge aller syntaktisch korrekte Formeln $For0_\Sigma$ iterativ

## Semantik

- <mark style="background: #FFB86CA6;">Interpretation</mark> ist eine Abbildung $I: \Sigma \rightarrow \{W, F\}$
- <mark style="background: #FFB86CA6;">Auswertung</mark> ist eine Abbildung $val_I: For0_\Sigma \rightarrow \{W, F\}$
- <mark style="background: #FFB86CA6;">Modell</mark> ist eine Formal $A$ mit $val_I(A) = W$
- Eine Formel <mark style="background: #FFB86CA6;">Allgemeingültig</mark> gdw sie Modell für jede Interpretation $I$ ist
- Eine Formel ist <mark style="background: #FFB86CA6;">erfüllbar</mark> wenn sie Modell für eine Interpretation $I$ ist
$$F\ ist\ allgemeingültig \Leftrightarrow \neg F\ ist\ unerfüllbar$$
- <mark style="background: #FFB86CA6;">Boolesche Funktionen</mark> sind Funktionen $\{W,F\}^n \rightarrow \{W,F\}$ definiert über eine Formel $A$ mit $f_A(b) = val_I(A)$ mit $I(X_i) = b_i$ 
- <mark style="background: #FFB86CA6;">Basen</mark> sind Mengen aus Konstanten und Operatoren, mit denen alle booleschen Funktionen darstellbar sind

## Ableitungen

 - $M \vDash A$ gilt wenn jedes Modell von $M$ ein Modell von $A$ ist
	 - $M$ ist eine Menge korrekter Formeln
	 - $A$ ist eine einzelne Formel
- Formeln $A, B$ sind <mark style="background: #FFB86CA6;">logisch äquivalent</mark> wenn gilt $\{A\} \vDash B$ und $\{B\} \vDash A$

### Allgemeingültige Formeln
![[Pasted image 20241025121909.png]]
![[Pasted image 20241025121919.png]]

---

Origin: Formale Systeme
References: 
Tags: 
Created: 25.10.2024

