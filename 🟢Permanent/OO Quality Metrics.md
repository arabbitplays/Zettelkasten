# OO Quality Metrics

- An Object $X$ ist modeled by an Instance $x$ and properties consisting of methods and instance variables $p(x) = \{M_x\} \cup \{I_x\}$
- measure complexity of a class through
	- $n = |p(x)|$
	- length of inheritance tree
	- number of child class
	- coupling between classes
		- how much are the functions of other classes used
		- prevents modular design and reuse
	- response sets
		- the size of the set of methods called by methods of a class
		- testing and debugging is more complicated
	- lack of cohesion on methods
		- The numbers of method pairs that share variables minus the method pairs that do share variables
		- promotes encapsulation

## Antipatterns

- Isolated classes or package, that have no references to other classes or packages
- Cycles in the inheritance Graph

---

Origin:  Model Driven Software Development
References: [[Models]]
Tags: 
Created: 13.12.2024

