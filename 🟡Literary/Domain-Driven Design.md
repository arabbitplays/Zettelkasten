# Domain-Driven Design

## Introduction

1. Identify bounded context of application domains
2. For each domain
	1. Extract the domains ubiquitous language
	2. Destill domain model from that language
	3. Reflect the model in software using building blocks
	4. Employ [[Software Architecture]] to develop domain application
3. Deploy and link the application as indicated by context map
	1. Consider realising each domain application as a [[Service-Oriented Architecture#Micro-service Architecture | Microservice]]

- <mark style="background: #FFB86CA6;">Ubiquitous Language</mark>
	- a common language between technical experts and domain experts
- <mark style="background: #FFB86CA6;">Bounded Context</mark>
	- declares the scope for the language
	- depends on the domain (actors supported), team organization and the physical manifestation (code base, database schema)
- <mark style="background: #FFB86CA6;">Context Map</mark> 
	- relates common entities between bounded contexts

- Example: Web Shop Application
	- Bounded contexts: catalog, orders, user registration, accounting, shipping
	- Context Map: "Product" is common for catalog and orders, "Customer" is common for the other three

## Building Blocks

- patterns for encoding domain concepts in implementation

### Patterns for domain concepts

- <mark style="background: #FFB86CA6;">Entity</mark> denotes a domain concept with a unique identity
	- identity is preserved during store, load, transmission, ...
	- with continuity throughout its life cycle, making it traceable and accountable
	- customer, product, order, ...
- <mark style="background: #FFB86CA6;">Value Object</mark> denotes domain concept without identity
	- distinguishable only by the attribute values
	- is immutable, permits safe sharing, duplication and distribution
	- quantity, monetary amount, ...
- <mark style="background: #FFB86CA6;">Service</mark> denotes domain concept that encodes functionality
	- interface is defined in terms of entities and value objects
	- is stateless, regardless of operation / transformation
	- if not stateless, consider modelling as entity
	- customer manager, order manager, ...

### Patterns for support structures

- <mark style="background: #FFB86CA6;">Aggregate</mark> clusters related entities and value objects
	- defines root entities serving as a Facade
	- identity of the aggregate is derived from the root entity
	- ensures invariants and concurrent access
	- purchase order, shopping cart, ...
- <mark style="background: #FFB86CA6;">Factory</mark> provides means to create a domain concept
	- hides complexity of object construction
	- ensures products invariants
	- not applicable if construction is easy or client cares about implementation (construction strategy)
	- customer factory, shipment factory, ...
- <mark style="background: #FFB86CA6;">Repository</mark> permits finding domain concepts
	- allows for accessing all, subsets or individual items (complex queries)
	- usually backed by persistence mechanism
	- catalog, order repo, ...

## Domains

Types of domains:
- <mark style="background: #FFB86CA6;">Core Domain</mark>
	- crucial aspect of the domain model to solve a domain-related problem
	- all other support core domain
- <mark style="background: #FFB86CA6;">Shared Kernel</mark>
	- shared concepts between domains
	- maintained and evolved by multiple teams (coordination and integration)
- <mark style="background: #FFB86CA6;">Supporting domain</mark> 
	- concepts extracted from core, supporting the core domain
- <mark style="background: #FFB86CA6;">Generic Subdomain</mark> 
	- excapsulates most generic concepts, not belonging to the core

Types of interactions between domains
- a shared kernel can be used
- <mark style="background: #FFB86CA6;">Consumer/Supplier</mark>
	- downstream requests functionality from upstream team
- <mark style="background: #FFB86CA6;">Conformist</mark>
	- downstream "slavishly" adheres to domain model of upstream team
- <mark style="background: #FFB86CA6;">Anti corruption layers</mark>
	- downstream sets up a layer translating upstreams domain model
- <mark style="background: #FFB86CA6;">Open Host Service</mark>
	- define protocol to allow downstream services to use services from upstream team
- <mark style="background: #FFB86CA6;">Published language</mark>
	- formalize protocol to [[Domain Specific Language (DSL)]]

---

Origin: 
References: [[Software Architecture]], [[Model Driven Software Development (MDSD)]]
Tags: 
Created: 02.07.2025

