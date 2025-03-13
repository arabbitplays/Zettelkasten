# Model Quality

## Best Practices

- use inheritance and multiple inheritance to avoid repetition and factor out structures
	- never insert the same attribute or reference into two classes
- there should be a root element and every other element should be contained by exactly on other element
	- model should follow a tree structure
	- allows for clear responsibility of life cycle management
	- an element may have multiple possible containers
- the default should be directed references, navigability should be explicit
	- all classes should be reached by references
- named references can express different roles of a class
- type-safe enumerations instead of strings

## Metamodel Quality

- Quality improvement is a heavyweight process, as it requires the adaptation of the [[Model Transformations]], editors (see [[Xtext]]) and so on
- the correct level of abstraction is hard to hit and domain-specific
- modularisation can be measured through the cohesion within a package and the separation of different packages

### Antipatterns

- Isolated classes - classes that don't use other classes and are not used by other classes
- Isolated packages - packages without references
- Cycles in the inheritance graph

### Metrics

- Total number of classifiers
- Total number of elements in the XMI representation
- Number of element contained in the package
- Depth of packaging, the longest path from the root to an element
- Depth of inheritance (see [[OO Quality Metrics]])
- Depth of containment, the longest chain of containment references
- Number of containers per concrete class
- Total number of disjoint roots - ideally one

---

Origin: 
References: [[Model Driven Software Development (MDSD)]], [[Models]]
Tags: 
Created: 12.03.2025

