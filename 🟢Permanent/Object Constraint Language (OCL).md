# Object Constraint Language (OCL)

- OCL is a declarative specification language, used to define constraints on a [[Metamodel]] formally
- can be used for every [[Meta-Object Facility (MOF) |MOF]]-based metamodel
- the constraints can be evaluated <mark style="background: #D2B3FFA6;">side effect free</mark> and should be decidable

- constraints are defined for classes and evaluated for instances

## Invariants and conditions

- Invariants are constraints that are true for the whole lifetime of the object
```OCL
context <classifier>
inv [<constraint name>]: <Boolean OCL Expression>

context student
inv NoUnderage: self.age >= 16
```

- can also be used to define pre- and postconditions, but in the context of verification, [[Java Modelling Language (JML) | JML]] is more commonly used
```
context ATM::confiscateCard() 
pre: insertedCard <> null 
post: insertedCard = null and insertedCard @pre.invalid
```


## Types

![[Pasted image 20241115102624.png |300]]
- `allInstances()` gives all instances of a type -> should only be used on non-primitive classes
![[Pasted image 20241115102641.png |300]]
- sets have unique elements, ordered set and sequence have ordering


- strongly typed, have to adhere to the [[Liskov Substitution Principle]]

## Operations

- `=` equality, `<>` inequality, `AND OR NOT implies`
```OCL
if ...
	then ...
	else ...
endif
```
- `first() last() indexOf()` for ordered collections
- for types `oclIsTypeOf() oclIsKindOf()` checks if the object is the type or a subtype (for kindOf)
- Classic collection operations like `union() intersection()` and set transformations like `asSet()`
- Iterator Operations
	- `Set{1,2,3,4,5} -> select(x | x > 2) = Set{3,4,5}`
	- `collect` gives the values of a feature
		- `Set{Helbig, Ostermann} -> collect(firstName) = Bag{'Jakob', 'Juli'}`
	- `exists() one() forAll()` check if a statement is true for one, exactly one or all elements
	- `iterate` is a bit like [[Kombinatoren#Fold]] 
		- `iterate(i: Integer, sum: Integer = 0 | sum + 1)`

## Advanced Concepts

`let <name> : <type> = <expression> in ...`

---

Origin: Model Driven Software Development
References: [[Model Driven Software Development (MDSD)]]
Tags: 
Created: 15.11.2024

