# Cloud Computing

## Introduction

Scalable, network-centric abstracted IT infrastructure, platforms and applications as on-demand services.
The whole technology builds fundamentaly on compute and storage virtualization

![[Pasted image 20250627115714.png]]
## Core Characteristics

- five essential characteristics
	- elastic scalability
	- on-demand self-service
	- ubiquitous network access
	- resource pooling
	- measured service

- <mark style="background: #FFB86CA6;">scalability</mark> - high load can be countered by more resources
- <mark style="background: #FFB86CA6;">elasticity</mark> - a resource management system can provide resources according to varying demand

## Multi-Tenancy

- isolation of workloads and customers, but only through virtual resource sets, no physical separation
	- customers share the OS, hardware and so on
	- no separate applications, but different data and metadata that changes the appearance and behavior per customer
- <mark style="background: #FFB86CA6;">virtual machines using hypervisor</mark>
	- run multiple virtual machines on top of a hypervisor (control program)
- <mark style="background: #FFB86CA6;">containerization</mark>
	- instead of a hypervisor controlling multiple virtual OS, us a docker engine controlling multiple container
		- engine supports creating, linking and managing containers
	- each container has its own runtime env and system libs

## Service Delivery Models

- <mark style="background: #FFB86CA6;">Software as a Service (SaaS)</mark>
	- the consumer has the possibility to use the providers applications running on a cloud infrastructure
		- they are accessible through thin client interfaces (web browsers or program interfaces)
	- the consumer doesn't control anything about the cloud infrastructure, with the exception of limited, user-specific application configuration settings
	- for example IBM SmartCloud Solutions
- <mark style="background: #FFB86CA6;">Platform as a Service (PaaS)</mark> 
	- the consumer has the possibility to deploy self-created or acquired applications onto the infrastructure
		- they can be created using programming languages, libraries and tools supported by the provider
	- the consumer can not manage or control the underlying infrastructure, network, server or operating system
	- for example Microsoft Azure Web Apps
- <mark style="background: #FFB86CA6;">Infrastructure as a Service (IaaS)</mark>
	- the consumer has control over fundamental computing resources (storage, network, ...)
	- the consumer can run and deploy arbitrary software, even operating systems
	- the consumer has no control of the underlying cloud infrastructure
	- for example Amazon web services, Microsoft Azure VMs, ...

## Service Deployment Models

- <mark style="background: #FFB86CA6;">private</mark> cloud - customer and provider belong to the same organization
- <mark style="background: #FFB86CA6;">public</mark> cloud - customer and provider belong to different organizations
- <mark style="background: #FFB86CA6;">hybrid</mark>  cloud - combination of the both above
- <mark style="background: #FFB86CA6;">community</mark> cloud - stakeholders share resources to achieve common goals

## Architecture Principles

- often [[Parallel Machinemodels#MapReduce | Map Reduce]] is used as a parallelism model

- Decentralization - remove scaling bottlenecks and single points of failure
	- each component should be scalable on its own
- Autonomy - each component should be able to make decisions based on local information
	- loose coupling through message queues
- Controlled concurrency - operations should be designed in a ways that required no or limited concurrency control
- Controlled parallelism - work in a granularity that supports parallelism for improved performance and robustness
- failure tolerant - failure of components should be a normal mode of operation
	- externalize state so it can be resumed  after failure
	- visibility timeouts in message queues -> messages become visible to other consumers if the original one fails

---

Origin: 
References: [[Software Architecture]]
Tags: 
Created: 25.06.2025

