# SysML

- a graphical modeling language developed by the OMG
- supports specification, analysis, design, verification and valiation of systems including hardware, software, data, procedures, personnel and facilities
- Four pillars of SysML
	- Structure - block diagrams
	- Behaviour - Activity diagrams
	- Requirements - categorization and relations between requirements
	- Parametrics - constraints between the properties of values
- is a [[Unified Modelling Language (UML) | UML]] profile with some extensions
![[Pasted image 20250313091832.png]]

## Requirements

- can add user defined requirement categories like functional, interface or performance
![[Pasted image 20250313092154.png]]

## Blocks

- describe the structure of an element of the system
- multiple standard compartments of the block (horizontal separator lines)
	- properties (parts, references, values, ports)
	- operations
	- constraints
	- allocation from/to other model elements
	- requirements the block satisfies
- <mark style="background: #FFB86CA6;">Port</mark> - specify interaction point between blocks and parts
	- standard UML port - specifies a set of required operations and or signals
	- flow port - specifies what can flow in out out of the block/part
		- typed by block, value type of flow specification

## Activity

![[Pasted image 20250313092912.png]]

## Parametrics

- models constraints between value properties
- costraint parameters can be bound to values of blocks, like the vehicle mass can be bound to $m$

![[Pasted image 20250313093139.png]]

---

Origin: MDSD Vorlesung
References: 
Tags: 
Created: 13.03.2025

