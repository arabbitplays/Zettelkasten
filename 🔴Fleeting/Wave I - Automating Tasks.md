# Wave I - Automating Tasks

## Introduction

- focuses on the automating management tasks like self-optimization, self-healing, self-protection or self-configuration
- introduces the <mark style="background: #FFB86CA6;">MAPE-K</mark> loop and different forms of it

## Essential maintenance tasks

- <mark style="background: #FFB86CA6;">self-optimization</mark> is the capability to optimize resource, while providing the quality assignment
- <mark style="background: #FFB86CA6;">self-healing</mark> is the capability to detect and recover from faults
- <mark style="background: #FFB86CA6;">self-protection</mark> - protect against attacks and anticipate requirements
- <mark style="background: #FFB86CA6;">self-configuration</mark> - capability to automatically integrate new elements

## MAPE-K

![[Pasted image 20251106101520.png]]

- even multiple MAPE-K loops are possible, interacting in different patterns (example here would be a master-slave setup)
	- ![[Pasted image 20251106101825.png]]

## Automatic decision making

- for different properties (failure-rate, service cost, ...) define a utility preference function $p_i$ by the stakeholders and a property weight $w_i$ how important the property is
![[Pasted image 20251106102419.png | 500]]
$$U_c = \sum_i w_ip_i$$
- calculate for multiple configurations and pick the one with the highest utility

---

Origin: 
References: 
Tags: 
Created: 06.11.2025

