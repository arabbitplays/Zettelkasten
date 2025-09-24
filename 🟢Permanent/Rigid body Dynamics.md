# Rigid body Dynamics

## Introduction

## Newton's three laws of motion

- <mark style="background: #FFB86CA6;">inertia</mark> - object stays in rest or keeps moving with constant velocity when no force is applied
- <mark style="background: #FFB86CA6;">force</mark> 
	- is product of mass and acceleration $f = ma$
	- or equivalently force is change of momentum $f = \frac{\partial p}{\partial t}$
- <mark style="background: #FFB86CA6;">collision</mark> - when objects collide/exchange forces, the magnitude stays the same but the opposite direction

- <mark style="background: #FFB86CA6;">Newton Dynamics</mark> is a simulation of state variables
	- solve a set of differential equations to determine a new position after time interval $\Delta t$ (sometimes denoted $h$)

## Position calculation

- primary quantities: center of mass $c$, linear momentum $p_v = mv$
- constants: mass $m$
- derived quantities: velocity $v$
- linear forces acting on the point: force $f$

1. External forces on the point determine acceleration $a = f/m$ 
2. Update velocity by integrating acceleration $v = v_0 + \int a(t')dt'$ 
3. Update position by integrating velocity $c = c_0 + \int v(t')dt'$ 
- use [[Integration Schemes]] to calculate the integrals

## Rotation calculation

- Added quantities for rotation
- primary quantities: orientation $q$ (as [[Quaternions]], analog $c$), angular momentum $p_\omega = I\omega$ (analog $p_v$)
- constants: Inertia tensor $I$ (3x3 matric)
- derived quantities: angular velocity $\omega$, spin $\partial q / \partial t$ (quaternion)
- rotational force: torque $\tau$ (analog $f$)

- Angular momentum and velocity are both vectors, standing for the rotation axis
	- length encodes the amount of rotation / speed of the rotation respectivly
- a force at an offset of the center of mass $r$ can be decomposed into 
	- a linear force directly to the center of mass
	- torque around the axis $r \times f$
- <mark style="background: #D2B3FFA6;">updating the rotation has an analytical solution</mark> with  $q(t+\Delta t) = q(t) + exp(0,5 \Omega \Delta t)$
	- $\Omega$ is the pure quaternion to $\omega$
### Intertia Tensor $I$

- describes how hard it is to rotate an object around a given axis (analog to mass for linear momentum)
- compute an inertia tensor by
	- the [basic shape](https://en.wikipedia.org/wiki/List_of_moments_of_inertia#List_of_3D_inertia_tensors)
	- transformations
		- can compute inertia tensor for a rotated frame ($I' = RIR^\top$) or translated center of mass
	- combination
		- if two tensors are expressed to the same frame (center of mass and orientation) they can be componentwise added

- translate inertia tensor with respect to the origin to the center of mass $C$ (parallel axis theorem)
$$I_C = I_0 - m \begin{bmatrix} c_y^2+c_z^2 & -c_x c_y & -c_x c_z \\
        -c_x c_y & c_x^2+c_z^2 & -c_y c_z\\
        -c_x c_z & -c_y c_z & c_x^2+c_y^2 \end{bmatrix}$$

## Rigidbody Recipe

1. External force $f_k$ is applied to offset $r_k$ from center of mass $c$
	- vector add all $f_k$ to get $f$
	- sum all $\tau_k = r_k \times f_k$ to get $\tau$
2. Compute dependent quantities
	- $v = p_v / m$
	- $\omega = RI^{-1}R^\top p_\omega$ with $R$ being the rotation matrix to orientation $q$
		- this should happen in world space, that's the reason for the whole $R$ thing
3. Integrate (use [[Integration Schemes#Runge Kutta|RK4]])
$$q(t+\Delta t) = q(t)\cdot\exp\left(\frac{1}{2}\Omega\Delta t\right)$$
$$c(t+\Delta t) = c(t) + \int_{\Delta t} v(t) \mathrm{d}t$$
$$p_\omega(t+\Delta t) = p_\omega(t) + \int_{\Delta t} \tau(t) \mathrm{d}t$$
$$p_v(t+\Delta t) = p_v(t) + \int_{\Delta t} f(t) \mathrm{d}t$$

---

Origin: https://www.cs.cmu.edu/~baraff/pbm/pbm.html
References: 
Tags: 
Created: 16.09.2025

