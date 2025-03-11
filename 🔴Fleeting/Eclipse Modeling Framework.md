# Eclipse Modeling Framework

- Eclipse is a highly extendable IDE
	- Runtime in very minimal with an extension mechanism, sets of standard plugins are given in packages
- EMF is a framework for modeling and data integration in Eclipse
	- UI, code generation, task automation, extendability, persistence of models with XMI
	- Comes with an [[Meta-Object Facility (MOF) | EMOF]]-based [[Metamodel | Meta-Metamodel]] called <mark style="background: #FFB86CA6;">Ecore</mark>

## Ecore-based Metamodels

- can be generated through the project wizard
	- input is the model specification (UML, Java, XML, \*.ecore files)
	- generated meta model in XMI (\*.ecore) and a generator model (\*.genmodel)
		- generator model contains information for generators and is automatically synchronized 
- EMF contains mapping between Ecore Elements and Java classes and Interfaces
- Ecore has all important Java Datatypes (Including java.lang.Object) and its own types 
- Ecore has its own reflection mechanism similar to java.lang.reflect

```Ecore
// Setting attribute with the generated API
Student ebStudi = DiplomFactory.eINSTANCE.createStudent(); ebStudi.setMatrNr(1146018);

// Setting attribute with the refelctive API
EObject ebStudi = DiplomFactory.eINSTANCE.createStudent(); EClass studiClass = ebStudi.eClass(); ebStudi.eSet(studiClass.getEStructuralFeature("matrNr"), 1146018);
```

### Code Generation

- Ecore classes are [[Model Transformations | transformed]] into two construct, the interface class and the implementation class
![[Pasted image 20250311113905.png]]
- Automatic generation of
	- model implementation
	- editors and views for Eclipse
	- Junit Test Skeletons
- Handwritten code can be added
	- when the @generated annotion is removed, the method is not regenerated on changes

---

Origin: 
References: 
Tags: 
Created: 11.03.2025

