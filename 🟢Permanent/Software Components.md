# Software Components

## Introduction

A component is a unit of composition with [[Design by Contract | contracutally specified]] interfaces, which can be composed, deployed and and adapted without understanding its internals.

=> A whole system can be composed of components

## Component Model

- defines what a component is, how they are connected, how they communicate, ...
- only components developed for the same model can be used together
	- als components for a model form a <mark style="background: #FFB86CA6;">repository</mark>
- often comes with a <mark style="background: #FFB86CA6;">framework</mark> used to execute and connect components

## Technical Realisation

- many different realisations, but most are rather object-based then components based
	- -> no real concept above packages 
- java has no direct concept of components
	- mimic with packages, classes + dependency injection or facades

### Open Service Gateway Initiative (OSGi)

- OSGi offers bundles as a concept of components
	- basically a JAR file that offers an interface
	- the provided service can only be used when the bundle is explicitly required in the consumer bundle
	- provides a registry for bundles at runtime

### Web Services

- self-contained, self-describing modular applications that can be published and invoked via the web
	- self-contained -> no dependencies, functionality is exposed but implementation isn't
	- self-described -> machine-readable description to understand the interface
- can be seen as deployed web-services
- gives rise to [[Service-Oriented Architecture]]

## Palladio Component Model (PCM)

- PCM is a [[Domain Specific Language (DSL)]] for predicting performance at design time
- derives performance predictions based on [[Models]] and [[Model Views]] of the implementation, a environment model and a usage model
- <mark style="background: #FFB86CA6;">Service Effect Specification (SEFF)</mark>
	- description of external visible actions
	- <mark style="background: #FFB86CA6;">parametrization</mark> - describe resource usage in terms of abstract units (CPU, HD, NET) -> filled in with timing values as soon as the environment is specified
		- the same with usage definition, is defined as "number of elements" or "byte size" 
- components define interfaces via [[Design by Contract]]
- components can be composed from other components
- Different jobs
	- Component developer: Components and SEFFs 
	- Software Architect: Assembly 
	- System Deployer: Resource environment 
	- Domain Expert: Usage

---

Origin: 
References: [[Software Engineering Index]], [[Software Architecture]]
Tags: 
Created: 29.05.2025

