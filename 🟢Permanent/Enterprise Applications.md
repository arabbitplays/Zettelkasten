# Enterprise Applications

## Introduction

- Software that supports businesses
	- mainly about concurrent display, manipulation and storage of large amounts of persistent data
	- for example payroll system, online shops, CRM, tracking systems, ...
- interfaces to other systems
- at times very complex and changing business logic
- often classic layered [[Software Architecture]] with presentation, domain and data source

## Patterns

- common patterns in enterprise apps can be clustered in families
- only make a starting point for solutions
- multiple patterns of one family should not be mixed

### Domain Logic
	How to represent the business rules?

- <mark style="background: #FFB86CA6;">Transaction Scripts</mark>
	- all logic for one transaction in one procedure
	- <mark style="background: #BBFABBA6;">easy to implement and connect to data sources</mark>
	- <mark style="background: #FF5582A6;">doesn't scale with complexity</mark>
	- <mark style="background: #FF5582A6;">often has duplicate code</mark>
- <mark style="background: #FFB86CA6;">Domain Model</mark>
	-  design the domain layer using the domain [[Models |Model]]  
	- very object oriented, identify concepts and place logic in them
	- collaboration between objects to complete a transaction
	- <mark style="background: #BBFABBA6;">good organization of complex logic</mark>
	- <mark style="background: #FF5582A6;">mapping to data source is more complex</mark>
- <mark style="background: #FFB86CA6;">Table Module</mark>
	- One class handles all business logic for one data table
	- called with a record set (see below)  form the DB
	- <mark style="background: #BBFABBA6;">straight forward mapping of the data</mark>
	- <mark style="background: #BBFABBA6;">naturally separates different concepts</mark> 
	- <mark style="background: #FF5582A6;">no object instances, which is bad for complex logic</mark>

- When to use what?
	- Depends on the complexity of the domain logic
	- domain model scales the best
	- mapping to the data source and experience of the developers are secondary factors
### Data Source Architecture
	How to separate domain logic and data source

- <mark style="background: #FFB86CA6;">Record Set</mark> (basic pattern)
	- just an in-memory representation of table data
		- can be passed through the whole system
	- store all rows and columns in the instance
	- not trivial to be strongly typed
	- often created by frameworks or platform (for example as a JDBC result)
- <mark style="background: #FFB86CA6;">Table Data Gateway</mark>
	- one instance to handle one table in the DB
	- should cover all CRUD methods
	- map method parameters to  a SQL statement and execute the command
	- <mark style="background: #BBFABBA6;">useful for Transaction Scripts</mark>
- <mark style="background: #FFB86CA6;">Active record</mark>
	- brings data and functionality together
	- every object knows how to read and write their data from/to the DB
	- one static finder method to create an active record
	- does not work well with inheritance
	- <mark style="background: #BBFABBA6;">works well for simple domain logic</mark>
	- <mark style="background: #FF5582A6;">DB scheme and Active Record must be an 1:1 mapping</mark>
	- <mark style="background: #FF5582A6;">no separation of concerns</mark>
- <mark style="background: #FFB86CA6;">Row Data Gateway</mark>
	- one object as the gateway to one row of the table
	- one finder class to create the gateways from the DB
	- all details regarding the data source access are hidden behind the interface
	- use an <mark style="background: #FFB86CA6;">identity map</mark> to reduce lookups
		- sits between the finder and the DB and stores the loaded objects in a map
	- <mark style="background: #BBFABBA6;">good target for automatic code generation of the meta data of the DB (whole DB access can be built automatically</mark>
- <mark style="background: #FFB86CA6;">Data Mapper</mark>
	- a layer of mappers that moves data between objects and the DB
	- ![[Pasted image 20250625111932.png]]
	- mapper scan often be created by code generation
	- <mark style="background: #BBFABBA6;">best separation and clean usage</mark>
	- <mark style="background: #FF5582A6;">full featured mappers can be hard to write -> use existing one</mark>
	- especially useful in [[Model Driven Software Development (MDSD)]]

- When to use what?
	- For Transaction Scripts, the Gateways are a good fit
	- For Domain Models, if the logic is simple use active records, else use data mappers
	- For Table Modules, use table data gateway

### Object-relational (O/R) Structural Patterns
	Mapping of OO structures (inheritance, ...) onto relational DB, especially when using Domain Model & Data Mappers

- <mark style="background: #FFB86CA6;">Single Table Inheritance</mark>
	- represent inheritance as a single tables with all fields of all various classes
	- <mark style="background: #BBFABBA6;">simple DB scheme, no joins, no changes when fields are moved</mark>
	- <mark style="background: #FF5582A6;">unused fields, tables get large, only one namespace</mark>
- <mark style="background: #FFB86CA6;">Class Table Inheritance</mark>
	- One table for each class, with keys to the base class table
	- <mark style="background: #BBFABBA6;">easier to understand, all columns are relevant, easy relationship between domain model and DB schema</mark>
	- <mark style="background: #FF5582A6;">loading means touching multiple tables, refactoring more complicated</mark>
	- <mark style="background: #FF5582A6;">supertypes can become bottleneck</mark>
- <mark style="background: #FFB86CA6;">Concrete Table Inheritance</mark>
	- one table for every concrete class
	- ![[Pasted image 20250625112943.png]]
	- <mark style="background: #BBFABBA6;">one objects needs one table,  each on eis self contained without irrelevant fields</mark>
	- <mark style="background: #FF5582A6;">refacotring of supertypes needs changing all tables</mark>
	- <mark style="background: #FF5582A6;">queries on superclasses can need very complex joins</mark>

- When to use what?
	- depends on access pattern, tradeoff between data duplication and structure and speed

---

Origin: 
References: 
Tags: 
Created: 25.06.2025

