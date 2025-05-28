# Clean Code

## Introduction

Principles for clean coding, that make code bases better understandable, maintainable, expandable and testable!
[[OO Quality Metrics]] can be used to test for these principles.

## [[SOLID Principles]]

## Commenting

- Comments should be
	- explaining legal issues, performance issues, algorithms or intent
	- warning from consequences or importance
	- informative regarding todos 
- besides that, good naming of intermediate variables and methods should make code readable
	- not redundant comments that have to be maintained too

## Law of Demeter

- avoid long object chains
```
obj1.getObj2().getObj3().doSomething()
```
- code depends then on the class structure, which is volatile and changes a lot
- only call stuff on the parameters or direct components of the current class

## Other laws

- Don't repeat yourself (DRY)
	- duplicate code is harder to maintain and error prone due to different evolution
- Keep it simple, stupid (KISS)
	- Makes code easier to understand and thus use
- You ain't gonna need it (YAGNI)
	- only implement requested features, as everything costs to implement, test and maintain

---

Origin: 
References: 
Tags: 
Created: 28.05.2025

