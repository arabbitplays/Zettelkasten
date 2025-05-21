# Design of computer systems

## Introduction


## Areas of Application

- personal mobile devices (PMD)
	- for example tablets and smartphones
	- energy efficency is very important 
	- size of the device is relatively small
- desktop computing
	- wide spectrum of applications
	- interactive realtime applications regarding graphics, video and audio
- server and high performance computing
	- very computation and data intensive applications
	- have to be scalable
	- High demands on availability and reliability
- embedded systems
	- micro-processors, embedded in cars, household appliances, ...
	- can be very critical to be realtime (guarantees reaction in x ms)
	- tailored for a small set of applications
	- Internet of Things (IoT) is a special case with high demands of communication capabilities

## Computing power

- the <mark style="background: #FFB86CA6;">CPU time</mark> is the time needed by the CPU, to run a program
	- depends on the instruction count ($IC$)
		- determined by the instruction set architecture and compiler technology
	- the cycles per instruction ($CPI$) 
		- hard to determine through the complexity of modern CPUs (for example cache hierarchy)
		- depends on the processor organisation and the instruction set architecture
	- and the machine cycle time ($T_c$)
		- depends on the semiconductor technology and the processor organisation
$$T_{exe} = IC * CPI * T_c$$
- <mark style="background: #FFB86CA6;">throughput</mark> is the count of jobs completed in a given time interval

## Dependability

- <mark style="background: #FFB86CA6;">mean time to failure (MTTF)</mark> depends on the probability of survival
- <mark style="background: #FFB86CA6;">Probability of survival</mark> $R(t)$ is the probability that a flawless system (at $t = 0$) stays uninterrupted flawless until time $t$
- <mark style="background: #FFB86CA6;">mean time to repair (MTTR)</mark>
- <mark style="background: #FFB86CA6;">mean time between failures (MTBF)</mark> $MTBF = MTTF + MTTR$
- <mark style="background: #FFB86CA6;">availability V</mark> $$V = \frac{MTTF}{MTBF}$$
- <mark style="background: #FFB86CA6;">fault tolerance</mark> is the ability to achieve a goal even with a given number of faulty subsystems

---

Origin: 
References: 
Tags: 
Created: 13.05.2025

