## Introduction

- VL 1
- Global Or / And
	- Jeder schreibt ne 1 wenn $A[i]$ wahr ist
	- $O(1)$
- Maximum
	- $n^2$ PEs die alle Vergleiche machen und $n$ PEs die ein Globales And machen
	- $O(1)$
- Reduction (for an associative operation)
	- ![[Pasted image 20250326114023.png | 300]]
	- $O(log n)$ with efficiency $1 / log n$
	- <mark style="background: #FFB86CA6;">Brents Priniciple</mark> - reduce $n/p$ elements sequentialy and then the above
		- inefficient algorithms get efficient when using less PEs

##  Matrix Multiplication

- Naive parallelization needs $n³$ PEs
- DNS Algo 
	- Split Matrix in $N \times N$ matrices of size $n/N \times n/N$
	- compute result with two broadcasts and a reduction
		- ![[Pasted image 20250326115513.png | 300]]
	- <mark style="background: #BBFABBA6;">saves communication -> good for small matrices</mark>

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
## Sorting

- Vl 4 ff
- <mark style="background: #FFB86CA6;">Fast Inefficient Ranking</mark>
	- Like the maximum, broadcast your element to everyone, calc $A_i \geq A_j$ and reduce to get the number of smaller elements ($O(\alpha\ log(p))$)
	- Also possible to do this with Brents Principle
		- ![[Pasted image 20250327141915.png]]
		- $O(\alpha\ log(p) + \beta \frac{n}{\sqrt{p}} + \frac{n}{p}log(\frac{n}{p}))$ 
			- $\beta \frac{n}{\sqrt{p}}$ through the bigger messages; because only rows or columns are sent, the length has the square root
			- $\frac{n}{p}log(\frac{n}{p})$ because of the local sorting
		- Local ranking with the two sorted arrays $r$ and $c$ can be done in $O(|r| + |c|)$
		- <mark style="background: #BBFABBA6;">the fastest for low counts of elements per PE</mark>
- <mark style="background: #FFB86CA6;">Quicksort</mark>
	1. Pick a pivot (choose PE random weighted by the local element count, choose element random)
	2. partition locally into small elements $a$ and big elements $b$
	3. Calculate number of small and big elements $n_a, n_b$ through 2 reductions
	4. $k' = \frac{n_a}{n_a + n_b}$ PEs should work on small elements, round $k'$ smart to minimize load inbalance
	5. send $a$ and $b$ to the right PEs, split them up if needed
	6. Keep on working on the small or the big elements, depending if the own index is smaller or bigger then $k$
	- $\frac{n}{p} (log\ n+\beta log\ p) + \alpha log^2 \ p$
	- <mark style="background: #FF5582A6;">Its bad that the data is sent log times</mark>
	- <mark style="background: #BBFABBA6;">local work is theoretical optimal</mark>
- <mark style="background: #FFB86CA6;">Sample Sort</mark>
	- Base Idea:
		1. Find $p-1$ splitters
		2. Every PE creates $p$ buckets with the elements $v_k < d_i \leq v_{k+1}$ in bucket $k$ (binary search)
		3. All-to-all communication to send all the $k$-th buckets to PE $k$
		4. Sort locally
	- Picking the splitters
		1. Pick $a * p$ samples ($a = \frac{log(n)}{\epsilon^2}$)
		2. Sort the samples
		3. pick every $a$-th sample as a splitter
	- How big $n$ has to be so that the algo is efficient depends on the used sorting algo for the samples
		- best is fast inefficient ranking with $n \geq \frac{p^2 \beta}{log(p)T_{compr}}$
	- <mark style="background: #BBFABBA6;">Only has to send all the data one time</mark>
	- <mark style="background: #FF5582A6;">p startup overheads</mark>
- <mark style="background: #FFB86CA6;">Multiway merging</mark>
	- Base Idea:
		1. Sort local data
		2. Pick perfect splitters (multi-sequence selection)
		3. Send parts to the right PE and merge locally
		- ![[Pasted image 20250328100626.png | 300]]
	- Picking the splitters
		- On Shared Memory: PE $i$ selects element with global rank $k = i \frac{n}{p}$
			1. Pick random pivot $v$
			2. Split each sequence through binary search of v
			3. Determine in which half $k$ is, and do recursion until the intervals are trivial
			- ![[Pasted image 20250328101254.png | 400]]
			- $O(\frac{n}{p} log(\frac{n}{p}) + p\ log(n)\ log(\frac{n}{p}) + \frac{n}{p}log(p))$
				- local sorting + splitter selection ($p$ binary searches over $\frac{n}{p}$ elements and $log(n)$ recursion levels)
				- is efficient for $n > p^2log(p)$
		- On Distributed Memory: PE $i$ searches the pivots for all selection in his local data (translation of the shared memory approach)
			1. Binary search all pivots
			2. Vector reduction to find out in which half for which pivot the search continues
- <mark style="background: #FFB86CA6;">CRCW Theoretical Sampling Sort</mark>
	1. Sampling and splitter selection
	2. Allocate buckets twice as big as expected size
	3. write to random position in the buckets
	4. compactify with prefix sums
	5. Recursion
	- <mark style="background: #BBFABBA6;">theoraticaly achieves logarithmic time</mark>

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

## Priority Queue und Branch and Bound

- Applications
	- Priority driven Scheduling
	- [[Branch-and-Bound]]
	- Heuristik parallelelzation of Dijkstra
- Goal: Bulk insert and delete min in $O(log(n) + log(p))$

- VL 8 und 9 und 13
- <mark style="background: #FFB86CA6;">Naive Implementation</mark>
	- Each PE has a sequential priority queue
	- $\Omega(p(\alpha + log\ n))$
- <mark style="background: #FFB86CA6;">Local Queues approach</mark>
	- Every PE has a local PQ $Q_1$
	- Insert sends the element to a random PE
	- removeMin finds the $p$ globally smallest elements and assigns them to a PE
		- take a sample of $log(p)$ elements from each local queue ($Q_0$)
		- find $p$ smallest elements $e_i$ and check if $max\ e_i > min\ Q_1 @ j$ (see selection algo below)
			- if not then repeat
			- if yes, then reinsert the rest of $Q_0$ and use the $e_i$ as a result
		- assign them through a prefix sum
- <mark style="background: #FFB86CA6;">Better local queues approach</mark>
	- Split local queue in $Q_0$ and $Q_1$
	- Insert elements into $Q_0$
		- move $Q_0$ into $Q_1$ every $log(p)$ iterations
	- removeMin
		- add $min(Q_1)$ to $Q_0$ until the $p$ elements in $Q_0$ are smaller then $min(Q_1)$
		- select the $p$ globally smallest elements of $Q_0$ (see selection below)
		- assign them through a prefix sum
	- both opertations in $O(t_{coll} + log(\frac{n}{p})$
- <mark style="background: #FFB86CA6;">Selection Algorithm</mark>
	- find the $k$ smallest elements in $Q$
	- take a $\sqrt p$ sample, sort it with fast inefficient ranking
	- take two splitters $u = k/n |s| + \Delta$ and $l = k/n |s| - \Delta$
	- whp is $|Q_{<u}| < k$ and $|Q_{<l}| > k$ so select $Q_{<u}$ and find the $k - |Q_{<u}|$ smallest elements in $Q_{>l, <u}$ (constant recursions)
	- $O(\frac{n}{p} + T_{coll})$
	- ![[Pasted image 20250330101053.png | 350]]
- <mark style="background: #FFB86CA6;">Async PQ</mark>
	- Accept insertions but buffer them
	- Do a bulk delete min but hold the result in a buffer
- <mark style="background: #FFB86CA6;">Communication Efficient PQ</mark>
	- Insert into local queue $O(log(n))$
	- find $k$ smallest elements similar like in merge sort ($O(log^2(n))$)
		- but without assigning them to the PEs - depends on the inbalance, myb somewhere else is random distribution
- <mark style="background: #FFB86CA6;">Shared Memory PQs</mark>
	- $cp$ local PQs
	- insert into a random QP with locking, keep searching until a lock-free queue is found
	- delete smallest elements from $c$ PQs and return the smallest one
	- cache problems
		- increase locality through insertion and deletion buffers
		- <mark style="background: #FFB86CA6;">stickyness</mark> - stick to a set of queues for some consecutive opertations

## List Ranking

- Vl 13
- <mark style="background: #FFB86CA6;">Pointer Doubeling</mark>
	- p = n und CREW PRAM
	- $R(i)$ is the distance to the last element
	- $Q(i)$ is a pointer to a later element, in the beginnign just the successor
	- nutze für Base Cases Solver von anderen Algos
	- Sehr viel Arbeit
- Independend set removal
	- Inpedend Set: Weder pre noch successor ist schon im set
	- Löse die Instanz ohne das Independend Set, danach ist der Rest schnell aufgefüllt weil der Rank vom Successor ja bekannt ist
	- Lineare Arbeit mit schlechten konstanten Faktoren
- Ruling Set List Removal

## MST

- Vl 14 15
- The Jarník-Prim Algorithm und Kruskal
	- inherently sequential
- Boruvka’s Algorithm
	- Contraction
		- Präfix Summe: Jede Star Root ist ne 1, jede andere 0 
- Filter Kruskal
	- Filter ist grundlegende Idee, dass Kanten in leichte und schwere partitioniert werden
		- Auf den leichten wird eine Zwischenlösung berechnet
		- Wenn eine schwere einen Kreis in der Lösung schließt kann sie verworfen werden

## Load Balancing

- Vl 15 16
- Next Fit Parallel (mit und ohne splitting)
- Master Worker Scheme
- Randomized
- Load Stealing + das ganze abstrakte Baumproblem Modell