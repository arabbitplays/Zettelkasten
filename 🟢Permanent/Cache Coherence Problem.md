# Cache Coherence Problem

## Introduction

- with two processors and private [[Cache]]s, the copies in the caches must by in sync with the value in the main memory
	- even when one processor writes a new value to the address
- a cache is cache coherent when a read access always results in the value of the last write access

## Protocols

- <mark style="background: #FFB86CA6;">Snooping protocols</mark> - a cache controller watches the bus and checks if requested memory blocks are in the own cache
- <mark style="background: #FFB86CA6;">Directory-based protocols</mark> - the state of a memory block is tracked in a global or multiple local tables
- <mark style="background: #FFB86CA6;">Write-update protocols</mark> - all copies have to be updated after a write access, at latest when the value is read again
	- very communication heavy
- <mark style="background: #FFB86CA6;">Write-invalid protocols</mark> - all other copies of the data have to be invalidated on a write access
	- the changed address together with an invalidate signal are sent over the bus -> cache-controller read this and remove the cache line when it is hit

In the following, a write-back cache is assumed.

### MESI-Coherency Protocol

- is a snooping and a write-invalid protocol
- has different signals to handle cache events
	- invalidate - remove cache lines with the same address from all local caches
	- shared - signals that a requested block is already loaded in a cache
	- retry - signals that the requested block has been changed and the new value is in a local cache as a dirty line
- every cache line has 2 bits of state
	- shared vs exclusive - determines if an invalid signal has to be sent when the cache line is modified
		- when loading the line, other cache controllers can signal a shared signal, which makes the line shared
	- modified - the dirty bit, means that if an access is snooped, the line has to be copied in the main memory
	- invalid - the line is invalid and can be replaced by another one

### Directory-based Protocol

- global table: bit vector with a bit for every local cache, showing if the cache has a copy of the data
- distributed tables: every node has a table for its local memory
- table entries have state bits: shared, uncached, modified
	- when modified, the "owner" of the last update is stored too
- on write access, the processor holding the table for the address can inform all processors with the block in the cache to invalidate the cache


---

Origin: 
References: [[Memory Consistency Models]]
Tags: 
Created: 13.08.2025

