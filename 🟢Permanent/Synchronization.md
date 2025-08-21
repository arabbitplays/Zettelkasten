# Synchronization

## Introduction

- avoid [[Deadlocks]] and make weakened [[Memory Consistency Models]] possible through manual ordering of memory operations
- all synchronization routines build on hardware primitives
	- special hardware that allows for uninterruptible manipulation of memory

- [[Atomare Operationen]] are ones that can not be interrupted or split in two parts
	- avoids race conditions and makes race condition free synchronization possible
- <mark style="background: #FFB86CA6;">critical sections</mark> are sections where race conditions would happen without syncing

## Hardware Primitive

- Special assembly operation: test & set
	- checks if a register has the value 0
		- if yes, aquire a lock for a critical section and write 1 in the register
		- else, wait

## Synchronization Routines 

- [[Condition Variables]]
- [[Locks]]
- [[Semaphores]]

---

Origin: 
References: [[Operating System Index]]
Tags: 
Created: 13.08.2025

