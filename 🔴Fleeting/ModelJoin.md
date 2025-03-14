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
	- the expression defines the selection of elements and the target metamodel
	- operators are aligned with [[Structured Query Language (SQL) | SQL]] or rather [[Relationale Algebra]] with `join`, `keep` (projection) and `where` (selection)

- two attributes are <mark style="background: #FFB86CA6;">join conforming</mark> if it has the same type and the same multipicity
- two instances fulfil <mark style="background: #FFB86CA6;">instance-confomity</mark> if they carry the same values for their join-conforming attributes

- the <mark style="background: #FFB86CA6;">natural join</mark> results in a target class that contains all join-conforming attributes and for all instances with conforming attribute values, there is an instance in the target model
- the outer join in
---

Origin: MDSD Vorlesung
References: [[Models]]
Tags: 
Created: 14.03.2025

