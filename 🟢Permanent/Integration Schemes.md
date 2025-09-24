# Integration Schemes

## Introduction

- given a quantity $\phi$ with a derivative $\frac{\partial \phi}{\partial t} = f(t, \phi)$ and an initial value $\phi(t_0) = \phi_0$
- we are discretising time $t_0, t_1, \dots$ with step size $\Delta t$ and calculate $\phi_n = \phi(t_n)$
$$\int_{t_n}^{t_{n+1}} \frac{\partial \phi}{\partial t}dt=\phi_{n+1} - \phi_n$$

## Common Approximations

Explicit Euler:
$$\phi_{n+1} - \phi_n = f(\phi_n, t_n)\Delta t$$
Implicit Euler:
$$\phi_{n+1} - \phi_n = f(\phi_{n+1}, t_{n+1})\Delta t$$
Midpoint Rule:
$$\phi_{n+1} - \phi_n = f(\phi_{n+0,5}, t_{n+0,5})\Delta t$$
Trapezoid Rule:
$$\phi_{n+1} - \phi_n = \frac{1}{2}(f(\phi_n, t_n) + f(\phi_{n+1}, t_{n+1}))\Delta t$$
![[Pasted image 20250916123014.png]]
- Implicit Euler and Trapezoid is generally not applicable 
	- they depend on the future time step, that needs to be calculated specific for every differential equation

## Runge Kutta

Heun's method (predictor-corrector method, 2nd order Runge Kutta):
1. Calculate predictor like the explicit Euler method
$$\phi^* = \phi_n + f(\phi_{n}, t_{n})\Delta t$$
2. Correct the estimation with the now available $f(\phi^*, t_{n+1})$ like the trapezoid rule
$$\phi_{n+1} - \phi_n = \frac{1}{2}(f(\phi_n, t_n) + f(\phi^{*}, t_{n+1}))\Delta t$$

RK4 (iterative predictor-corrector method, 4th order Runge Kutta) 
$$\begin{align}
\phi_{n+1} &= \phi_n + \frac{1}{6} ( k_1 + 2k_2 + 2k_3 + k_4)\\
  k_1   &= \Delta t \cdot f(t_n,              \phi_n)\\
  k_2   &= \Delta t \cdot f(t_n + \Delta t/2, \phi_n + k_1/2)\\
  k_3   &= \Delta t \cdot f(t_n + \Delta t/2, \phi_n + k_2/2)\\
  k_4   &= \Delta t \cdot f(t_n + \Delta t,   \phi_n + k_3)
\end{align}$$
---

Origin: 
References: 
Tags: 
Created: 16.09.2025

