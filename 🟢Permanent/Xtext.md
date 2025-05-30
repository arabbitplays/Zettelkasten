# Xtext

- framework for the definition of textual languages
- provides complete infrastructure with a compiler, linker and an editor with syntax highlighting, autocompletion, ...

- XText definition of a [[Domain Specific Language (DSL)| DSL]] 
```Xtext
grammar edu.kit.ipd.sdq.Student with org.eclipse.xtext.common.Terminals 

import "http://sdq.kastel.kit.edu/diplom"

Student returns Student: 
	’Student’ name=STRING 7 
	’<<’ 
		(’Nr:’ matrNr=INT)?
		’studies:’ studies=StudiesType 
	’>>’; 

enum StudiesType returns StudiessType: 
	BACHELOR = ’Bachelor’ | MASTER = ’Master’ | DIPLOMA = ’Diploma’ | STAATSEXAMEN = ’ Staatsexamen’;
```
- the language can the be written in the standard editor like so
```
Student "Erik Burger" << 
	Nr: 1146018 
	studies: Diploma 
>>
```

---

Origin: 
References: [[Domain Specific Language (DSL)]]
Tags: 
Created: 11.03.2025

