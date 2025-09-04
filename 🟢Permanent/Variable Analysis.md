# Variable Analysis

## Introduction

- analysis how important the [[Memory Consistency Models | consistency]] of shared variables is in a parallel program
- goal: parallelyze a loop through domain partition
- the basic decision tree is:
	- local
	- shared
		- independent
		- dependent
			- reduction variable
			- locked variable
			- ordered variable
- <mark style="background: #FFB86CA6;">local variables</mark> are initialized for every iteration through a loop (like `i`)
- shared variable are <mark style="background: #FFB86CA6;">indepenent</mark> if every iteration only reads it or it is an array and every iteration used another element of the array

## Reduction variables

- is only used in a single associative and commutative operation
- for example summing all elements in an array
- global reduction operations can be used to still parallelize such a loop

## Locked Variable

- the read and write order is not important for the final value of the variable
- for example finding the maximum of and array
- critical section where this variable is written must be locked

## Ordered Variable

- order of read and write access through the iterations is important
- directly forces a sequential execution of the loop
- loop can still be optimized through guards
![[Pasted image 20250904152214.png | 400]]

---

Origin: 
References: [[Design of parallel programs]], [[Cache Coherence Problem]], [[Memory Consistency Models]]
Tags: 
Created: 04.09.2025

