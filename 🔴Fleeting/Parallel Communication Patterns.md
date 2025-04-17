# Parallel Communication Patterns

## Broadcasting

- <mark style="background: #FFB86CA6;">Naive Implementation</mark>
	- One message to everyone in time $(p-1)(\alpha + n \beta)$
- <mark style="background: #FFB86CA6;">Binomial Tree </mark>
	- if the message was already received, send to $i + 2^k$ for all remaining $k$
	- runs in time $(\lceil log(p) \rceil)(\alpha + n \beta)$
	- <mark style="background: #BBFABBA6;">good for many PEs</mark>
- <mark style="background: #FFB86CA6;">Linear Pipeline</mark>
	- Split message of length $n$ into $k$ pieces
	- receive piece $j$ from PE $i-1$ and send piece $j-1$ to PE $i+1$
	- runs in time $(k + p - 2)(\alpha + \frac{n}{k}\beta)$, with optimal $k$ its $n \beta + p \alpha + 2 \sqrt{np \alpha \beta}$
	- <mark style="background: #BBFABBA6;">Good for very large messages</mark>
- <mark style="background: #FFB86CA6;">Binary Tree Pipeline</mark>
	- receive piece $j$ from parent and send it first to the left, then to the right child
	- level $j$ is reached after $2j$ steps, the next package comes every three steps, so the algorithm runs in $(2 \lfloor log(p) \rfloor + 3(k-1))(\alpha + \frac{n}{k} \beta)$
- <mark style="background: #FFB86CA6;">Full duplex fibonacci tree pipeline</mark>
	- Fibonacci Tree reduces time to wait for the next package
	- receive piece $j$ from the parent, send $j-1$ directly to the right child
	- then send piece $j$ to the left child
	- runs in $\alpha d + 3(k-1))(\alpha + \frac{n}{k} \beta)$
	- $2n \beta + d \alpha + 2 \sqrt{np \alpha \beta}$ with $d = \lfloor log_\Phi(p) \rfloor$
- <mark style="background: #FFB86CA6;">23-Broadcast</mark>
	- use two binary trees, where every leaf on the one is inner node of the other
	- <mark style="background: #BBFABBA6;">all nodes can send and receive</mark>
	- ![[Pasted image 20250327122233.png | 300]]
	- optimal time
- <mark style="background: #FFB86CA6;">ESBT Broadcast</mark>
	- Edge Disjoint Binomial Trees
	- Structure PEs as a Hypercube ($p = 2^d$)
		- decompose into $d$ ESBTs
	- PE $0$ distributes packets to the roots, from there its a binomial tree broadcast
	- In step $i$ there is communication is dimension $i\ mod\ d$
	- optimal with $n \beta + d \alpha + 2 \sqrt{np \alpha \beta}$

## Präfix Sum

- <mark style="background: #FFB86CA6;">Linear Pipeline</mark> like in Broadcasting
- <mark style="background: #FFB86CA6;">Hypercube</mark>
	- Always communicate along one dimension (dimension $k$)
		- send the current running sum
	- if the k-th bit of the PE is set, then the running sum is added to the local result
	- $(\alpha + n \beta) log(p)$
- <mark style="background: #FFB86CA6;">Pipelined Binary Tree</mark>
	- Needs an inorder numbering
	- ![[Pasted image 20250329102833.png | 200]]
	- Upwards-Phase calculates sum over whole subtree $i' \dots i''$ (reduction)
	- Downwards-Phase calculates final results $1 \dots i$ (more general broadcast)
- Can be done with<mark style="background: #FFB86CA6;"> 23 Trees </mark>too
	- because the numbering is inorder for both trees
## Gossiping and All-Reduce

- VL 7
- Gossiping -> every PE has a message, in the end every PE should have every message
- All-Reduce -> every PE has a message, in the end every PE should have the reduction result
- <mark style="background: #FFB86CA6;">Hypercube Algorithm</mark>
	- Like the prefix sum one, but the running results always get concatenated (or reduced in the case of all-reduce)

## h-Relation

- $h$ is defined as the max number of packets communicated by one PE
	- $h_{in}(i) = \# packets\ received\ from\ PE\ i$
	- $h_{out}(i) = \# packets\ sent\ by\ PE\ i$
	- simplex model: $h = max_p\ h_{in}(i) + h_{out}(i)$
	- duplex model: $h = max_p\ max(h_{in}(i), h_{out}(i))$
- lower bound for PACKAGE-wise delivery: $h(package\ size * \beta + \alpha)$

- VL 8
- Für Nachrichten gleicher Länge
	- <mark style="background: #FFB86CA6;">Hypercube Algorithm</mark>
		- Communicate in dimension $d-1$ down to $0$
			- send all messages needed in the $j-D$ - subcube 
		- $log(p)(\frac{p}{2}n\beta + \alpha)$
			- Good for short messages as they are send multiple times
	- <mark style="background: #FFB86CA6;">1-Factor Algorithm</mark>
		- In each round let pairs of PEs exchange their messages for each other
			- with odd $p$ one PE is idle
			- with even $p$, the idle PE communicates with the one "extra" PE
		- $p(n\beta + \alpha)$
			- optimal for $n \rightarrow \infty$ but $p$ startups
- Für Nachrichten unterschiedlicher Länge
	- <mark style="background: #FFB86CA6;">Ostrich Algorithm</mark>
		- Just send all messages async into the communication network
		- With the definition of BSP its just $L + gh$ but it is not clear what $L$ and $g$ are
		- <mark style="background: #FF5582A6;">inconsistent</mark>
	- <mark style="background: #FFB86CA6;">Coloring based Algos</mark>
		- duplex model
			- Model $h$-relation as bipartite multigraph
				- every PE is a node on the left as a sender and on the right and a receiver
				- every directed edge is a sent package
			- Theorem: an edge coloring exists with $h$ colors
			- Algo: for $i \in [1, h]$, send packages with color $i$
			- <mark style="background: #FF5582A6;">edge coloring is expensive to compute</mark>
			- <mark style="background: #FF5582A6;">using packages increases the startups</mark>
			- <mark style="background: #BBFABBA6;">is optimal for package wise delivery</mark>
		- simplex model
			- Model $h$-relation as multigraph
				- every PE is a node
				- every edge is a sent package (undirected)
			- coloring is not optimal anymore
				- ![[Pasted image 20250329111056.png | 300]]
	- <mark style="background: #FFB86CA6;">2 Phase Algorithm</mark>
		- make a irregular all-to-all into two regular all-to-all
		- split every message into $p$ pieces, construct messages with one piece of every original message -> they are all the same length
		- after all-to-all, regroup the messages into messages that have the same receiver -> they are all the same length
		- ![[Pasted image 20250329111716.png | 400]]
		- <mark style="background: #FF5582A6;">a lot of copying and factor 2 more communication</mark>
	- <mark style="background: #FFB86CA6;">Non-Preemptive</mark>
		- greed approach: just send a message if both receiver and sender are idle
		- $k\alpha + 2h\beta$
			- $k$ is max number of messages a PE is involved in
			- $2h\beta$ is a 2-approx
		- <mark style="background: #BBFABBA6;">no unneccessary messages in the network</mark>
		- <mark style="background: #FF5582A6;">needs centralized scheduling</mark>


---

Origin: 
References: 
Tags: 
Created: 17.04.2025

