# Connection Networks

## Introduction

- Connect components of [[Design of computer systems | computer systems]]  or even multiple computer systems
	- allows communication and cooperation between components
- components can be processor chips or cores, [[Cache | Caches]], Memory Modules, ...

## Areas of Application

- <mark style="background: #FFB86CA6;">On-Chip Networks</mark>
	- connect registers, caches, processor cores and processor cores to multichip modules
	- small area, mostly producer specific
- <mark style="background: #FFB86CA6;">System / Storage Area Networks</mark>
	- connect connect processors with memory elements in a multi processor system and storage and I/O components in server systems
	- the base for supercomputers and the deciding factor for the [[Parallel Machinemodels]]
- <mark style="background: #FFB86CA6;">Local Area Network (LAN) and Wide Area Network (WAN)</mark>
	- connect autonomous systems in a local area (facility, campus, ...) or global area respectively
	- see [[Schichtensystem]] for more on that

## Basic Definitions

- nodes of the network are either host (or end) systems or intermediate systems
- a <mark style="background: #FFB86CA6;">switch</mark> connects a node to neighboring nodes over links
	- can have buffers to allow for multiple entries to send to the same exit
- a <mark style="background: #FFB86CA6;">link</mark> is a set of physical lines for the transfer of digital information
	- the width of a link is the number of bits that can be transferred in on cycle
- every node has a <mark style="background: #FFB86CA6;">network interface (NI)</mark> that is connected to a switch
	- used to send, receive and process messages
- messages consist of a <mark style="background: #FFB86CA6;">payload</mark> and <mark style="background: #FFB86CA6;">metadata</mark> like the receiver, message type or [[CRC Prüfsummen]]
- messages are often split into <mark style="background: #FFB86CA6;">packets</mark> of equal size that are summarized to a whole message by the receiver
	- there are request, response and acknowledgement packets
- [[Protokolle]] define the rules of a transmission


- open design questions:
	- [[Network Topology]] - which paths are available?
	- Routing - how is the best way through a network found?
	- Arbitration and flow control - how a conflicts over a resource resolved, messages buffered and buffer overflows prevented?

## Network Parameters & Performance Aspects

- bandwidth - bits per second
- diameter - longest shortest path between two nodes
- node degree of nodes
- average shortest path length between two nodes
- hardware complexity
- extendability - how many more nodes are needed to extend the network topology (for hypercubes double the amount of nodes, for a ring its only one)
- scalability - how well does a network keep its properties when it is extended
- redundancy - how many links can fail until nodes are not reachable anymore
- latency of a packet - time for the transmission, consisting of startup overhead, routing time, time of flight, transmission time (time between the arrival of the first and the last bit) and receiving overhead
---

Origin: 
References: [[Distributed Memory Multiprocessor]] 
Tags: 
Created: 12.08.2025

