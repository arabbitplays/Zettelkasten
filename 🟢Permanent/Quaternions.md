# Quaternions

## Introduction

Analogous to [[Complex Numbers]] in 4 dimensions
$$q = a + bi + cj + dk = a + \mathbf{q} \in \mathbb{H}$$
$$i^2 = j^2=k^2 = ijk = -1 \implies ij = k,\ ji = -k,\ \dots$$
The <mark style="background: #FFB86CA6;">conjugate</mark> is defines as
$$q^* = a - \mathbf{q}$$
## Multiplication

$$q_1q_2 = a_1a_2 - \mathbf{q_1} \cdot \mathbf{q_2}+a_1\mathbf{q_2}+a_2\mathbf{q_1}+\mathbf{q_1} \times \mathbf{q_2}$$
- So for <mark style="background: #FFB86CA6;">pure quaternions</mark> (with scalar part $a=0$) its
$$q_1q_2 = -\mathbf{q_1} \cdot \mathbf{q_2}+\mathbf{q_1} \times \mathbf{q_2}$$

## Rotation Properties

- a <mark style="background: #FFB86CA6;">unit quaternion</mark> ($||q|| = 1$) can be expressed in terms of a unit vector $\mathbf{q}$:
$$q = cos(\theta/2)+sin(\theta/2)\mathbf{q}$$
- so for a unit quaternion $q$ and a pure quaternion $v$,
$$qvq^*$$
- is a rotation of $v$ around $\mathbf{q}$ by $\theta$ degree

- we interpret the imaginary part as 3D space: $\mathbb{R} = \{x\mathbf{i}+y\mathbf{j}+z\mathbf{k}\ |\ x,y,z \in \mathbb{R}\}$
- so we rotate in the canonical planes spanned by two basis vectors with the 3 unit quaternions
$$cos(\theta)+\mathbf{i}sin(\theta),\ cos(\theta)+\mathbf{j}sin(\theta),\ cos(\theta)+\mathbf{k}sin(\theta)$$
- or formulated in analogy to Eulers formula:
$$e^{\mathbf{i}\theta},\ e^{\mathbf{j}\theta},\ e^{\mathbf{k}\theta}$$

- alternatively, take a unit vector $\mathbf{u}\in \mathbb{R}$, then $\mathbf{u}=u_x \mathbf{i}+u_y \mathbf{j}+u_z \mathbf{k}$ is directly a unit quaternion and
$$e^{\mathbf{u}\theta/2}ve^{-\mathbf{u}\theta/2}$$
- results in a rotation of $v$ around $u$ by $\theta$ degree

 - <mark style="background: #D2B3FFA6;">Multiple rotations can be chained by simply multiplying the quaternions</mark>

## Interpolation

- done via <mark style="background: #FFB86CA6;">spherical linear interpolation</mark>
$$slerp(p, q, t)= \frac{sin((1-t)\theta)}{sin(\theta)}p + \frac{sin(t\theta)}{sin(\theta)}q$$

---

Origin: 
References: [[Complex Numbers]]
Tags: 
Created: 16.09.2025

