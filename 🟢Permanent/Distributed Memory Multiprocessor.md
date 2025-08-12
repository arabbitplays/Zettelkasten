# Distributed Memory Multiprocessor

## Introduction

- no common memory or address space
- communication over messages sent over [[Connection Networks]] (see [[Network Topology]])
- can basicaly scale indefinitly, only capped by the connection network

## Structure

- each computation node consists of one processor or even a [[Uniform Memory Architecture (UMA)]]
	- has its own local memory $M$ 
	- is naturally asynchronous

### Network Costs

- Modelling the whole network structure is complicated ([[Network Topology]])
	- in practice, bandwidth and interconnections are plenty enough to assume constant costs for every communication partner -> <mark style="background: #FFB86CA6;">Fully connected point-to-point</mark>
- $T_{Comm}(m) = \alpha + m \beta$ for message length $m$
- Destinction between 
	- <mark style="background: #FFB86CA6;">half-duplex</mark> - send OR recieve from another PE
	- <mark style="background: #FFB86CA6;">telephone</mark> - send and recieve from PE $j$
	- <mark style="background: #FFB86CA6;">duplex</mark> - send and recieve from any PE

---

Origin: 
References: 
Tags: 
Created: 14.05.2025

