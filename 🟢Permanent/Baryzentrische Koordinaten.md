# Baryzentrische Koordinaten

- gegeben $k$ Punkte $P_1, \dots, P_k \in \mathbb{R}^n$
- Wenn ein Punkt gegeben ist mit $Q = \lambda_1 P_1 + \dots + \lambda_k P_k$ und $\lambda_1 + \dots + \lambda_k = 1$ sind die $\lambda$ die Baryzentrischen Koordinaten
![[Pasted image 20241105121049.png | 200]]
- es gilt $A_\Delta(Q, P_1, P_2) = 0,5 |P_1 - Q||P_2 - Q|sin(\phi) > 0$ wenn $Q$ im Dreieck liegt
- und $\lambda_1 = \frac{A_\Delta(Q, P_2, P_3)}{A_\Delta(P_1, P_2, P_3)}, \dots$

- Test ob $Q$ im Dreieck liegt: berechne $\lambda_i$ durch die Teilflächen, $Q$ ist im Dreieck gdw. $\lambda_1, \lambda_2, \lambda_3 \geq 0$
- Interpoliere Farben and den Vertices: Berechne $\lambda_i$ und es gilt $c_Q = \lambda_1 c_1 + \lambda_2 c_2 + \lambda_3 c_3$

---

Origin: Computer Grafik I
References: [[💡Resources/📦Zettelkasten/🟢Permanent/Raytracing]]
Tags: 
Created: 05.11.2024

