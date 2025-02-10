# Unified Modelling Language (UML)

- a [[Meta-Object Facility (MOF) | MOF]]-based standard that defines a [[Metamodels|metamodel]]  for software engineering
- Interchange format: UML Diagram Interchange
- Has no formal semantics, only natural language descriptions
- The UML Infrastructure defines the basic language constructs (with [[Model Driven Architecture |MDA]] as a framework)

![[Pasted image 20241030183840.png]]

## Profiles

- UML is general purpose -> good for most purposes but not ideal for every one
	- Profiles can be seen as a middle path between the usage of UML and the definition of a custom MOF-based metamodel
- A profile is a package that extends UML or adapts to a specific domain, platform, ...
	- extends Elements of type `Metaclass` and add constraints
	- application can be seen as a package import -> application of multiple profiles is possible
- A <mark style="background: #FFB86CA6;">stereotype</mark> defines how a class can be extended
	- the application to a class is call <mark style="background: #FFB86CA6;">extension</mark> and marked with a filled arrow
	- can contain attributes called <mark style="background: #FFB86CA6;">tags</mark> and the values of a stereotype instance are called <mark style="background: #FFB86CA6;">tagged values</mark>
	- <mark style="background: #D2B3FFA6;">cannot be extended by other stereotypes</mark> but it can be abstract and the specialized

![[Pasted image 20241111091459.png |300]]
![[Pasted image 20241111091618.png |300]]

- Profiles vs. Custom [[Metamodel]] 
	- No general guideline, depends on the set of necessary adaptions
	- <mark style="background: #BBFABBA6;">profiles are very light-weight, allow for extension but not modification</mark>
	- <mark style="background: #BBFABBA6;">Extended models are always valid UML instances</mark>
	- <mark style="background: #BBFABBA6;">UML tools can be used while modelling</mark>
	- <mark style="background: #BBFABBA6;">there are already existing profiles for many domains</mark>
	- <mark style="background: #FF5582A6;">less flexible</mark>
	- <mark style="background: #FF5582A6;">concepts of UML are still valid even if they have no meaning in the domain</mark>

## UML Infrastructure

- UMD infrastructure library defines a core that can be used to describe other metamodels like MOF and UML itself
	- contains two packages: Core for basic concepts and Profiles for adaption mechanisms
- Sub-packages of core:
	- PrimitiveTypes: defines Integer, Boolean, String, UnlimitedNatural
	- Basic: defines central stuff like class, attribute, package, operation
	- Abstractions: Concepts such as generalization, instantiation, restriction, cardinality, ...
	- Constructs: Base concept of association

## Generalization

- Partitionings of generalizations - multiple generalizations are grouped into a set
	- overlapping vs disjoint - if disjoint there are no instances that are instances of multiple classes of the generalization set
	- complete vs incomplete - did all subclasses have been specified
- a generalization set can be associated with a <mark style="background: #FFB86CA6;">power type</mark>
	- instances of a powertype are subclasses of the general class

---

Origin: 
References: [[Metamodels]] [[Meta-Object Facility (MOF)]]
Tags: 
Created: 30.10.2024

