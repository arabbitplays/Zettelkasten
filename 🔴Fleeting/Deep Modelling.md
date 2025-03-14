# Deep Modelling

- <mark style="background: #FFB86CA6;">Strict metamodelling</mark> is a modelling approach where every model is the instance of exactly one metamodel (resulting in the 4 layer hierarchy often used by [[Unified Modelling Language (UML) | UML]] or other [[Meta-Object Facility (MOF) | MOF]]-based metamodels)
- Deep modelling introduces two modes of classification, <mark style="background: #FFB86CA6;">linguistic</mark> ($L_i$) and <mark style="background: #FFB86CA6;">ontological</mark> ($O_i$)
	- strict metamodelling in each dimension
	- every ontological layer in $L_i$ is called <mark style="background: #FFB86CA6;">model</mark>
	- all models in $L_i$ are called the <mark style="background: #FFB86CA6;">ontology</mark> 
	- Elements are now called <mark style="background: #FFB86CA6;">clabjects</mark> as they are calsses AND objects 
	- <mark style="background: #FF5582A6;">The layers are counted the other way around, from abstract (0) to concrete (n)</mark>
- Linguistic layers define meta concepts for the modelling process
	- each layer defines the language for the layer down below
	- those are the "normal" layers of meta-metamodel, metamodel and model
- Ontological Layers define domain specific, real-world concepts and their classification

- <mark style="background: #FF5582A6;">Classic problem: The power of a locomotive is given by the series, so this is a restriction of instances of instances</mark>
	- possible solutions are stereotypes of power types, but both are not concise and scale badly

- Deep Instantiation Soution: Assign <mark style="background: #FFB86CA6;">potencies</mark> (non negative integer) to clabjects, attributes and values
	- potency of clabjects defines over how many levels it may have instances
	- potency of features is called <mark style="background: #FFB86CA6;">durability</mark> and defines over how many levels it is present in the instances of the clabject
	- potency of attribute values is called <mark style="background: #FFB86CA6;">mutability</mark> and it defines over how many levels a value may be changed from the default

![[Pasted image 20250314142840.png]]
- this is now two liguistic layers (model and metamodel) and three ontological layers (The concept of series, the concrete series and a locomotive of the series)

## The language core

- The <mark style="background: #FFB86CA6;">pan-level model</mark> is a linguistic metamodel that defines $L_0$
	- its the abstract syntacx of [[Unified Modelling Language (UML)]]
	- The <mark style="background: #FFB86CA6;">Level agnostic Modelling Language (LML)</mark> brings a general purpose concrete syntax and uniform concepts for all ontological levels
- In LML objects and classes are merged to clabjects
	- they have onto
---

Origin: MDSD Vorlesung
References: [[Metamodel]], [[Meta-Object Facility (MOF)]]
Tags: 
Created: 14.03.2025

