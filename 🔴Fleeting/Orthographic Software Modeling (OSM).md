# Orthographic Software Modeling (OSM)

- all artifacts describing a system can be understood as [[Model Views]]
	- even program codes, as it has no information about for example the deployment
- Idea: all information is present in a <mark style="background: #FFB86CA6;">Single Underlying Model (SUM)</mark>, all views are generated from this model
	- information is displayed and manipulated only through specific views 
	- the underlying formalism is the SUM [[Metamodel]]


- In other engineering disciplines, orthograhpic projection is used for technical drawings
	- apply this in software engineering -> <mark style="background: #FFB86CA6;">Orthographic Software Modeling (OSM)</mark>
	- ![[Pasted image 20250315091725.png | 200]]
- Basic principles of OSM
	- Dynamic view generation
		- views are created on the fly through [[Model Transformations]] and not persisted
		- a view is <mark style="background: #FFB86CA6;">editable</mark> if the transformation is bidirectional
	- Dimension-based view navigation
		- views are organized as hypercubes, where a sub-cube represents a view type and a specific cell represents a view
		- dimensions should be orthogonal to each other
		- ![[Pasted image 20250315092325.png | 300]]
	- View-oriented methods
---

Origin: MDSD Vorlesung
References: [[Model Views]]
Tags: 
Created: 15.03.2025

