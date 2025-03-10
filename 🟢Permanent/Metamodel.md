# Metamodel

- metamodels are models that make statements about modelling
- they are defined in a formal language
- specification of metamodels
	- abstract syntax
		- what are the constructs of the metamodel, independend of the specific presentation (ie the concept of a class in UML)
	- concrete syntax
		- describes the presentation of te abstract syntax
		- can define multiple presentations (graphical, textual, ...)
	- static semantic
		- all the rules and constraints not expressed in the abstract syntax (for example with [[Object Constraint Language (OCL)]])
	- dynamic semantic
		- describes the meaning of constructs, often in natural language

## Modelling Layer

- every metamodel is a model -> it can have a "meta-metamodel"
- the last one is often <mark style="background: #FFB86CA6;">self-descriptive</mark>
	- a class diagram can describe the abstract syntax of a class diagram
	- natural language can describe natural language
- some approaches have fixed number of layers ([[Unified Modelling Language (UML)| UML]])
	- other have varible many layers (deep modelling)
- The [[Meta-Object Facility (MOF)]] is the meta-metamodel for most common models

---

Origin: Model Driven Software Development
References: [[Models]]
Tags: 
Created: 30.10.2024

