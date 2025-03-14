# ModelJoin

- a [[Domain Specific Languages (DSLs) | DSL ]] with human-readable textual concrete syntax
- instances of heterogenous [[Metamodel | Metamodels]] can be merged into user defined views
	- basicly [[Model Transformations]] from two source models to one target view model
- does not change the source models

```ModelJoin
THETA JOIN imdb.Actor WITH library.Person 
	WHERE Actor.name = Person.firstName.concat(’ ’).concat(Person.lastName) 
	AS jointarget.Person { 
		KEEP ATTRIBUTES imdb.Person.firstName 
		KEEP ATTRIBUTES imdb.Person.lastName 
		KEEP SUBTYPE library.Borrower AS TYPE jointarget.Customer 
}
```
- combines the Person class of a metamodel "library" with the Actor Class of a metamodel "imdb"
---

Origin: MDSD Vorlesung
References: [[Models]]
Tags: 
Created: 14.03.2025

