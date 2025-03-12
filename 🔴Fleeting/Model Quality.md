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

---

Origin: 
References: [[Model Driven Software Development (MDSD)]], [[Models]]
Tags: 
Created: 12.03.2025

