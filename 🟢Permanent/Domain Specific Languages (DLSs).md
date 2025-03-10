# Domain Specific Languages (DLSs)

- with <mark style="background: #FFB86CA6;">domain specific modeling languages</mark>, the application structure, behaviour and requirements are specified
	- The are not general purpose like java, but less expressive and more compact and precise

## Textual Languages

- Graphical concrete syntax ist often just a subset of the abstract syntax
	- diagrams also can get very big
- with textual language, existing tools for editing text (versioning, autocompletion, highlighting, ...) can be used
- textual DLSs can be 
	- <mark style="background: #FFB86CA6;">grammar based</mark> like [[Xtext]] - define the language with a grammar definition, the [[Metamodel| Metamodel]] is then derived from the grammar
	- <mark style="background: #FFB86CA6;">mapping based</mark> like Xpand - create a metamodel and define how the element sof the model map to the syntax of the language 

---

Origin: Model Driven Software Development
References: [[Model Driven Software Development (MDSD)]]
Tags: 
Created: 06.12.2024

