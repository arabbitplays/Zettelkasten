# Eclipse Modeling Framework

- Eclipse is a highly extendable IDE
	- Runtime in very minimal with an extension mechanism, sets of standard plugins are given in packages
- EMF is a framework for modeling and data integration in Eclipse
	- UI, code generation, task automation, extendability, persistence of models with XMI
	- Comes with an [[Meta-Object Facility (MOF) | EMOF]]-based [[Metamodel | Meta-Metamodel]] called <mark style="background: #FFB86CA6;">Ecore</mark>

## Ecore-based Metamodels

- can be generated through the project wizard
	- input is the model specification (UML, Java, XML, \*.ecore files)
	- generated meta model in XMI (\*.ecore) and a generator model (\*.genmodel)
		- generator model contains information for generators and is automatically synchronized 

---

Origin: 
References: 
Tags: 
Created: 11.03.2025

