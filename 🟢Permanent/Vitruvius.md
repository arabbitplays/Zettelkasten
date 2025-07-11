
# Vitruvius

**Vie**w-cen**tr**ic engineering **u**sing a **vi**rtual **u**nderlying **s**ingle model

- combines the synthetic and projective approaches to [[Model Views]]
- based on the SUM model introduced in [[Orthographic Software Modeling (OSM)]]
## Constructing a SUM

- the SUM Metamodel can be seen a a collection of [[Metamodel | metamodels]] and [[Model Transformations]] to construct different views from these metamodels
	- becomes virtual, ergo a <mark style="background: #FFB86CA6;">V-SUM</mark> model, as i doesn't exist as a concrete model but as a interconnected set of models and transformations
![[Pasted image 20250315093530.png]]

- creation process:
	- choose the Metamodels that should be used by the SUM
	- Specify the legacy views that are commonly needed
	- choose and specify the combined views especially needed by this system
		- specify the consistency rules
	- all of this is then combined into the SUM Metamodel
- [[Domain Specific Language (DSL)#Textual Languages| Textual Languages]] can be included through frameworks like [[Xtext]]
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
- consistency management through transformations
	- <mark style="background: #FFB86CA6;">change-based</mark> - changes to a model are observed and the transformation works on the sequence of changes
		- changes are recorded through the Ecore notification system
		- model monitor saves the changes, triggers the vitruvius framework which in turn executes consistency preservation transformations
	- for the consistency specifications, there are two types of languages
		- <mark style="background: #FFB86CA6;">mappings languages</mark> - declarative definition of relations between metamodels
			- each rule defines conditions (`check`) under which to check elements and properties they must fulfill (`enforce`)
			- <mark style="background: #BBFABBA6;">generate bidirectional transformations</mark>
			- <mark style="background: #FF5582A6;">limited expressional power</mark>
		- <mark style="background: #FFB86CA6;">reactions languages</mark> - imperative definition of actions for restoring consistency
			- every reaction defines repair routines (`match`) and actions for the change (`action`)
			- <mark style="background: #FF5582A6;">generate unidirection transformations</mark>
			- <mark style="background: #BBFABBA6;">turing complete, allows for arbitrary rules</mark>

---

Origin: MDSD Vorlesung
References: [[Orthographic Software Modeling (OSM)]], [[Model Views]]
Tags: 
Created: 15.03.2025


