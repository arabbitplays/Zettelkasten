# Model Transformations

- A <mark style="background: #FFB86CA6;">transformation</mark> is an automatic generation of a target model from a source model
- the<mark style="background: #FFB86CA6;"> transformation definition</mark> is a set of transformations that describe how the target model is generated
- a <mark style="background: #FFB86CA6;">transformation rule</mark> is a description on how one concept is transformed into the other

- allows for separation of domain and technology like in [[Model Driven Architecture (MDA) | MDA]]
- <mark style="background: #FFB86CA6;">endogenous</mark> transformations - transform between instances of the same [[Metamodel]] for optimization or refactoring
- <mark style="background: #FFB86CA6;">exogenous</mark> transformations - between instances of heterogenous metamodels for code generation or migration
- <mark style="background: #FFB86CA6;">horizontal vs vertical</mark> - if target and source lie on the same abstraction level
- <mark style="background: #FFB86CA6;">semantic vs syntactic</mark> - is it just parsing or does the transformation take the meaning into account

## Model transformation language

- used for the definition of model transformations
- they should be expressive but simple, performant, interoperable and standardized for standards like [[../🟢Permanent/Unified Modelling Language (UML).md | UML]] or [[../🟢Permanent/Meta-Object Facility (MOF).md | MOF]] 
- can be a functional language or a logical language, only when keeping track of state is very important, imperative languages are used

## Graph Transformations

- MOF-based Metamodels can be described as graph structures
- Graph Transformations abstract away specific transformation languages
- Rules or Productions consist of three graphs (left $L$, right $R$ and the glue graph $K$) where $K$ is included in $L$ and $R$
	- If the rule is applied to a graph $G$, find $L$ in $G$ and replace this part with $R$
	- $$r = <L \hookleftarrow K \hookrightarrow R>$$
![[Pasted image 20250310113423.png]]

## Queries, Views and Transformations (QVT)

- Based on EMOF and [[Object Constraint Language (OCL) | OCL]] as a query language 

---

Origin: Model Driven Development
References: [[Models]]
Tags: 
Created: 07.12.2024

