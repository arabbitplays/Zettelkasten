# SOLID Principles

## Introduction

- principles for writing clean code in the context of object oriented design
- their main goal is to make code more human readable and easy to understand

- **S**ingle Responsibility Principle (SRP) 
- **O**pen Closed Principle (OCP) 
- **L**iskov Substitution Principle (LSP) 
- **I**nterface Segregation Principle (ISP) 
- **D**ependency Inversion Principle (DIP)

## Single Responsibility Principle

- Every class should have one concern
- Bad smells: big classes with more than 200 lines and 15 methods/fields

### Command-Query-Separation

- functions should ether be <mark style="background: #FFB86CA6;">commands</mark> or <mark style="background: #FFB86CA6;">queries</mark>, not both
	- commands are actions, that have side effects (setter)
	- queries just give information back, without side effects (getter)

## Open Closed Principle

- classes should be open for extension but closed for modification
	- modify behavior through adding code, not changing old code

## Liskov Substitution Principle

- <mark style="background: #D2B3FFA6;">Instances of a class can always be substituted by an instance of a subclass</mark>
- Invariants can only be strengthened
- Preconditions can only be weakened
- Postconditions can only be strengthened
- Strongly related to [[Design by Contract]]

## Interface Segregation Principle

- <mark style="background: #FFB86CA6;">High cohesion</mark>: Interfaces should only be concerned with single concepts 
- <mark style="background: #FFB86CA6;">Interface pollution</mark>: Interfaces should not depend on other interfaces just because a subclass requires those
![[Pasted image 20250425124033.png | 400]]
## Dependency Inversion Principle

- everything should depend on interfaces/abstractions
- abstractions should not depend on details, but only the other way around
- example using [[Model-View-Controller (MVC)]]:

Problematic Version:
![[Pasted image 20250528180811.png | 400]]

Solution:
![[Pasted image 20250528180910.png]]

- <mark style="background: #BBFABBA6;">simplifies testing through the possibility of  mock implementations</mark>
- <mark style="background: #FF5582A6;">assumes good and stable interface abstractions are possible</mark>  

---

Origin: 
References:  Software Engineering Lecture 
Tags: 
Created: 24.04.2025


