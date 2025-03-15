
# Vitruvius

- combines the synthetic and projective approaches to [[Model Views]]
- based on the SUM model introduced in [[Orthographic Software Modeling (OSM)]]

## Constructing a SUM

- the SUM Metamodel can be seen a a collection of [[Metamodel | metamodels]] and [[Model Transformations]] to construct different views from these metamodels
![[Pasted image 20250315093530.png]]

- creation process:
	- choose the Metamodels that should be used by the SUM
	- Specify the legacy views that are commonly needed
	- choose and specify the combined views especially needed by this system
		- specify the consistency rules
	- all of this is then combined into the SUM Metamodel
- [[Domain Specific Languages (DSLs)#Textual Languages | Textual Languages]] can be included through frameworks like [[Xtext]]
	- for popular languages, grammars and metamodels exist
	- allows for the integration of versioning, diff/merge, ...
- <mark style="background: #FFB86CA6;">Flexible views</mark> can have a single (yellow) or multi-metamodel (red) scope
	- <mark style="background: #FFB86CA6;">projective scope</mark> - specify the types used in the view as well as their relation to the base metamodels
	- <mark style="background: #FFB86CA6;">selective scope</mark> - specify the elements for the view based on instance properties
	- needs rules of editability and proper synchronization to the base model
	- For example VT2:
		- projective scope: components from PCM, classes from UML, implements from CS
		- selective scope: all components and classes that are linked through the implements relation
		- editability: implements is editable, classes and components are write protected

---

Origin: MDSD Vorlesung
References: [[Orthographic Software Modeling (OSM)]], [[Model Views]]
Tags: 
Created: 15.03.2025


