# Bézier Curve Parameterisation

## Introduction

- Mathematically, Bézier curves get paramerized by $t$ which has no physical connection to the length along the arc 
- but for [[Animation]] it is practical to have a parameter that moves along the curve in constant speed

## Parameterisation by arc length

- be $x(t)$ a [[Bézier Curves | Bézier curve]], $s$ the arc length and $P(s)$ that searched curve over $s$
- define a mapping $A$ between the parameters
$$s = A(t),\ P(s) = x(A^{-1}(s))$$
- for $A$, we integrate the gradient magnitude along the curve
$$A(t) = \int_0^t |\nabla x(t')|dt'$$

---

Origin: 
References: [[Bézier Curves]]
Tags: 
Created: 15.09.2025

