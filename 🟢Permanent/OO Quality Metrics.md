# OO Quality Metrics

- An Object $X$ ist modeled by an Instance $x$ and properties consisting of methods and instance variables $p(x) = \{M_x\} \cup \{I_x\}$
- measure complexity of a class through
	- $n = |p(x)|$ 
		- estimator for the compexity of a class
	- length of the inheritance tree
	- number of child classes
		- more means more reuse, but at some point it may be a misuse of subclassing
	- coupling between classes - if $\{M_X\}$ uses method or variables from $\{M_Y\}$ or $\{I_Y\}$, $X$ and $Y$ are coupled
		- how much are the properties of other classes used
		- prevents modular design and reuse
		- makes testing harder
	- response sets - $RSC = |\{M\} \bigcup_i \{R_i\}|$ where $R_i$ is the set of methods called by the method $i$
		- the size of the set of methods called by methods of a class
		- testing and debugging is more complicated
	- lack of cohesion on methods
		- The numbers of method pairs that don't share variables minus the method pairs that do share variables
		- promotes encapsulation
		- lack of cohesion suggests a possible split of a class into two

## Antipatterns

- Isolated classes or package, that have no references to other classes or packages
- Cycles in the inheritance Graph
- giant classes or methods
- class A calls lots and lots of methods of class B (feature envy)

---

Origin:  Model Driven Software Development
References: [[Models]]
Tags: 
Created: 13.12.2024

