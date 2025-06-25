# Service-Oriented Architecture

## Introduction

Architectural style building on the idea of structuring a system in [[Software Components]].
Service-oriented architecture and micro-service architecture is not exactly the same, but both build on this idea and both will be introduced here.

Big plus sides is that every service can be deployed independently and each (micro-) service can be scaled independently

## Service-oriented Architecture (SOA)

- focuses on an enterprise level, where multiple applications are coupled 
- each service can have multiple responsabilities
![[Pasted image 20250529121555.png  | 300]]
- SOAP (Simple Object Access Protocol) 
	- message layout specification defining a uniform way of passing XML-encoded data 
- WSDL (Web Service Description Language) 
	- defines Web Services as collections of network endpoints or ports
	- port defined by associating network address with a binding 
- UDDI (Universal Description, Discovery and Integration) 
	- provides mechanism for clients to find web services 
	- basis for repository services for business applications

## Micro-service Architecture

- focuses on an application level
- each service has exactly one responsability
- communication over more lightweight mechanisms like HTTPS or REST APIs
- core principles
	- organized around business capabilities -> conways law: the system structure is a copy of the organizations communication structure
	- Products not projects -> DevOps: Teams that build the software deploy and run the software
	- Smart endpoints, dumb pipes -> focuses more on the well decoupled and cohesive endpoints then a very sophisticated messaging bus
	- Decentralized Governance -> produce useful tools that can be shared with a wider group
		- <mark style="background: #FFB86CA6;">Tolerant reader pattern</mark> - ignore unknown input elements and make minimum assumptions
		- <mark style="background: #FFB86CA6;">Consumer Driven Contracts</mark> 
			- Service implements a wide union of needs
			- a call before the actual call to the service specifies the actually needed service
	- Decentralize data management -> each service has its own database (can bring sync problems)
	- Infrastructure Automation -> continuous deployment and integration
	- designed for failure
		- monitoring if a service fails to resolve this quickly
		- redundancy through multiple instances of a service
	- evolutionary design -> service can be upgraded independently

- <mark style="background: #BBFABBA6;">Pros</mark> 
	- reinforce modular structure
	- independent deployment
	- technological diversity -> mix languages, databases, ...
- <mark style="background: #FF5582A6;">Cons</mark> 
	- Distributed systems harder to build and maintain
	- consistency 



---

Origin: 
References: [[Software Architecture]]
Tags: 
Created: 29.05.2025

