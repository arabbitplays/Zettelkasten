# Real-Time Systems

## Introduction

- mostly systems that monitor and control their environment 
	- often embedded systems
	- use sensors to capture data and actuators to change the system environment
- they must respond within specified times
	- processing data faster than it is captured (or buffer them)
	- react to the environment fast enough (e.g. Airbags)
- correct functioning of the system depends on the result AND when the result is provided
- in <mark style="background: #FFB86CA6;">soft real-time systems</mark> the result is degraded if it is not produced in the timeframe
- in <mark style="background: #FFB86CA6;">hard real-time systems</mark> the result is incorrect if it is not produced in the timeframe
- they are often designed as a stimuli/response system
	- stimuli occur (periodic like a polling of a sensor or aperiodic like an interrupt) and the system must produce a response fast enough
- different types of real-time systems
	- <mark style="background: #FFB86CA6;">Monitoring Systems</mark> act when a sensor gives an exceptional value
	- <mark style="background: #FFB86CA6;">Control Systems</mark> continuously  change actuators according to sensor values
	- <mark style="background: #FFB86CA6;">Data Aquisition Systems</mark> just read sensors for further data processing, but the period of the processing may be different (buffers)
- every sensor - actuator pair has different timing constraints, thus a real-time system is often implemented as multiple cooperating processes
	- controlled through [[Interrupts]] and [[Scheduling]]
- <mark style="background: #FFB86CA6;">random faults</mark> can just happen anytime, <mark style="background: #FFB86CA6;">systemtic faults</mark> are there by design
## Real-time Patterns

- a <mark style="background: #FFB86CA6;">channel</mark> is an architectural pattern like a pipeline where data is passed through and every steps makes relatively simple operations on the data
	- throughput can be increased through multiple channels
	- reliability can be increased through multiple channels working in various ways, achieving fault tolerance
	- safety can be increased through adding fault identification and safety measures to channels
- Without fail-safe state
	- <mark style="background: #FFB86CA6;">homogeneous redundancy</mark> - multiple sets of sensor-actuator pairs, switch automatically in case of failure -> against random faults
	- <mark style="background: #FFB86CA6;">heterogeneous redundancy</mark> - multiple sets of sensor-actuator pairs, but the channels are differently implemented to increase fault tolerance -> against random and systemic faults
- With fail-safe state
	- <mark style="background: #FFB86CA6;">Protected single channel</mark> - increase safety through error detection
		- assume fail-safe state if unresolvable failure is detected
	- <mark style="background: #FFB86CA6;">Monitor-Actuator Pattern</mark> - special case of heterogeneous where the channel and actuator are supervised by an actuator monitor sensor
		- monitor can shutdown the channel
		- softer version where the result is only approximated is called <mark style="background: #FFB86CA6;">Sanity-Check Pattern</mark>
		- (lightweight) protection against random and systemic faults
	- <mark style="background: #FFB86CA6;">Watchdog</mark> - channel has to send heart beat signal to watchdog, if it is missing too long, the channel is shutdown
		- protects against time-based faults and deadlocks
---

Origin: 
References: [[Reliability of Computer Systems]], [[Software Engineering Index]]
Tags: 
Created: 24.08.2025

