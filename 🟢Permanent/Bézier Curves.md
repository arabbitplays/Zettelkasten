# Bézier Curves



## Bernstein polynomials

$$B_i^n(u) = \binom{n}{i}u^i(1-u)^{n-i}\ or\ 0\ if\ i<0 \vee i > n$$

- some properties:
	- $B_i^n(u) \geq 0, u \in [0, 1]$ 
	- $\sum_{i=0}^n B_i^n(u) = 1$
	- $B_i^n(u) = u * B_{i-1}^{n-1}(u) + (1-u)B_i^{n-1}(u)$
- They form a basis of $\mathbb{P}_n$

- given 4 control points $b_i$, the cubic  <mark style="background: #FFB86CA6;">Bézier curve</mark> is given by
$$F(u) = \sum_{i=0}^3b_i B_i^3$$
![[Pasted image 20250128121020.png]]

## de Casteljau-Algorithm

- Algorithm to evaluate a Bézier curve efficently
- use the recursive definition of the Bernstein polynomials:
$$b_i^0 = b_i$$
$$b_i^1=(1-u)b_i^0 + ub_{i+1}^0$$
- can be used to subdivide a curve
	- ![[Pasted image 20250128121936.png | 200]]
	- The points $b_0^i$ are the controlpoints for the left Subcurve of the Bézier Curve

## Bézier Splines

- for more complex curves a high degree would be needed
	- numerical inprecision is a problem
	- every control point influences the result
- instead connect multiple curves with lower degree (ie degree 3)
	- this is called a <mark style="background: #FFB86CA6;">Bézier Spline</mark>

- given two Bézier curves with control points $b_i$ and $c_i$, their spline is 
- $C_0$ continuous if $b_n = c_0$
- $C_1$ continuous if $b_n-b_{n-1} = c_1-c_0$
- $C_2$ continuous if $b_{n-1}+(b_{n-1} - b_{n-2}) = c_1+(c_1-c_2)$
- <mark style="background: #FFB86CA6;">A-Frame</mark> Property if the spline is in $C_2$
	- ![[Pasted image 20250128123401.png | 400]]
	- The control points are fixed in a way that they always form an A ($b_1, b_2, c_1, c_2$ and the orange one)

- So if a $C_2$ splie is needed, only the tips of the A-frames can be given and all other points can be derived
	- ![[Pasted image 20250128123654.png | 400]]
	- This is called a <mark style="background: #FFB86CA6;">B-Spline</mark>

---

Origin: https://www.youtube.com/watch?v=aVwxzDHniEw&ab_channel=FreyaHolm%C3%A9r
References: 
Tags: 
Created: 28.01.2025

