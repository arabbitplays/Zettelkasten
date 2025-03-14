# Deep Modelling

- <mark style="background: #FFB86CA6;">Strict metamodelling</mark> is a modelling approach where every model is the instance of exactly one metamodel (resulting in the 4 layer hierarchy often used by [[Unified Modelling Language (UML) | UML]] or other [[Meta-Object Facility (MOF) | MOF]]-based metamodels)
- Deep modelling introduces two modes of classification, <mark style="background: #FFB86CA6;">linguistic</mark> ($L_i$) and <mark style="background: #FFB86CA6;">ontological</mark> ($O_i$)
	- strict metamodelling in each dimension
	- every ontological layer in $L_i$ is called <mark style="background: #FFB86CA6;">model</mark>
	- all models in $L_i$ are called the <mark style="background: #FFB86CA6;">ontology</mark> 
	- Elements are now called <mark style="background: #FFB86CA6;">clabjects</mark> as they are calsses AND objects 

- <mark style="background: #FF5582A6;">Classic problem: The power of a locomotive is given by the series, so this is a restriction of instances of instances</mark>
	- possible solutions are stereotypes of power types, but both are not concise and scale badly

- Deep Instantiation Soution: Assign <mark style="background: #FFB86CA6;">potencies</mark> (non negative integer) to clabjects, attributes and values
	- potency of clabjects defines over how many levels it may have instances
	- potency of features is called <mark style="background: #FFB86CA6;">durability</mark> and defines over how many levels it is present in the instances of the clabject
	- potency of attribute values is called <mark style="background: #FFB86CA6;">mutability</mark> and it defines over how many levels a value may be changed from the default

---

Origin: MDSD Vorlesung
References: [[Metamodel]], [[Meta-Object Facility (MOF)]]
Tags: 
Created: 14.03.2025

