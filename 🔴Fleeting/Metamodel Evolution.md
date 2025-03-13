# Metamodel Evolution

- just like programs, [[Metamodel | Metamodels]] are decaying over time through changing requirements and a dynamic environment
- other artifacts depend on the structure of the metamodel, like instances, transformations, templates. editors, etc.
	- they have to <mark style="background: #FFB86CA6;">co-evolve</mark>

- <mark style="background: #FFB86CA6;">atomic changes</mark> - smallest possible change (CRUD)
- <mark style="background: #FFB86CA6;">complex changes</mark> - combination of atomic ones, for refactoring, moving elements and so on

- <mark style="background: #FFB86CA6;">change-sequence</mark> is a sequence of $n$ atomic change steps $d_i$
- the <mark style="background: #FFB86CA6;">evaluation function</mark> is applying a sequence $D$ to a model $eval_D(M) = M'$
- sequences $D, D'$ are <mark style="background: #FFB86CA6;">equivalent (~)</mark> if $\forall M (eval_D(M) = eval_{D'}(M))$
- a sequence $D$ is <mark style="background: #FFB86CA6;">minimal</mark> if $\forall D'(D \sim D' \implies |D| \leq |D'|)$

## Determining Changes

- <mark style="background: #FFB86CA6;">delta-based</mark> - don't save $M'$ but only $M$ and a set of change steps $D$ referencing only $M$
	- record edits in the editor
	- <mark style="background: #BBFABBA6;">user intend is captured clearly</mark>
	- <mark style="background: #FF5582A6;">in general the resulting sequence is not minimal</mark>
- <mark style="background: #FFB86CA6;">state-based</mark> - both $M$ and $M'$ are know, find $D$ that references both models with differencing algorithm
	- <mark style="background: #BBFABBA6;">can be used with generated models</mark>
	- <mark style="background: #FF5582A6;">finding the sequence requires complex algorithm</mark>

## Co-Evolution

- model instances depend on the metamodel so they can break through changes
![[Pasted image 20250313101544.png | 350]]
- Severity classification
	- <mark style="background: #FFB86CA6;">model-preserving</mark> - $\underline{M}$ is a valid instance of $M'$
	- <mark style="background: #FFB86CA6;">safely model-migration</mark> - $\underline{D}$ is injective
	- <mark style="background: #FFB86CA6;">unsafely model-migration</mark> - $\underline{D}$ is not injective
- a change is a
	- <mark style="background: #FFB86CA6;">refactoring</mark> if a bijective mapping always exists
	- <mark style="background: #FFB86CA6;">constructur</mark> if an injective mapping always exists
	- <mark style="background: #FFB86CA6;">destructor</mark> if a surjective mapping always exists
## The Change Metamodel

- describes the abstract superclasses of possible changes to a metamodel
- complex changes have to be manually modeled
![[Pasted image 20250313100144.png]]

---

Origin: MDSD Vorlesung
References: 
Tags: 
Created: 13.03.2025

