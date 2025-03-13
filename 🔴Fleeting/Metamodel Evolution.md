# Metamodel Evolution

- just like programs, [[Metamodel | Metamodels]] are decaying over time through changing requirements and a dynamic environment
- other artifacts depend on the structure of the metamodel, like instances, transformations, templates. editors, etc.
	- they have to <mark style="background: #FFB86CA6;">co-evolve</mark>

- <mark style="background: #FFB86CA6;">atomic changes</mark> - smallest possible change (CRUD)
- <mark style="background: #FFB86CA6;">complex changes</mark> - combination of atomic ones, for refactoring, moving elements and so on

- <mark style="background: #FFB86CA6;">change-sequence</mark> is a sequence of $n$ atomic change steps $d_i$
- the <mark style="background: #FFB86CA6;">evaluation function</mark> is applying a sequence $D$ to a model $eval_D(M) = M'$
- sequences $D, D'$ are <mark style="background: #FFB86CA6;">equivalent (~)</mark> if $\forall M (eval_D(M) = eval_{D'}(M))$
- a sequence $D$ is <mark style="background: #FFB86CA6;">minimal</mark> if $\forall D'(D \~ D' \implies |D| \leq |D'|)$
---

Origin: MDSD Vorlesung
References: 
Tags: 
Created: 13.03.2025

