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

- Naive Implementation
	- One message to everyone in time $(p-1)(\alpha + n \beta)$
- Binomial Tree 
	- if the message was already received, send to $i + 2^k$ for all remaining $k$
	- runs in time $(\lceil log(p) \rceil)(\alpha + n \beta)$
	- <mark style="background: #BBFABBA6;">good for many PEs</mark>
- Linear Pipeline
	- Split message of length $n$ into $k$ pieces
	- receive piece $j$ from PE $i-1$ and send piece $j-1$ to PE $i+1$
	- runs in time $(k + p - 2)(\alpha + \frac{n}{k}\beta)$, with optimal $k$ its $n \beta + p \alpha + 2 \sqrt{np \alpha \beta}$
	- <mark style="background: #BBFABBA6;">Good for very large messages</mark>
- Binary Tree Pipeline
	- receive piece $j$ from parent and send it first to the left, then to the right child
	- level $j$ is reached after $2j$ steps, the next package comes every three steps, so the algorithm runs in $(2 \lfloor log(p) \rfloor + 3(k-1))(\alpha + \frac{n}{k} \beta)$
- Full duplex fibonacci tree pipeline
	- Fibonacci Tree reduces time to wait for the next package
	- receive piece $j$ from the parent, send $j-1$ directly to the right child
	- then send piece $j$ to the left child
	- runs in $\alpha d + 3(k-1))(\alpha + \frac{n}{k} \beta)$
	- $2n \beta + d \alpha + 2 \sqrt{np \alpha \beta}$ with $d = \lfloor log_\Phi(p) \rfloor$
- 23-Broadcast
	- use two binary trees, where every leaf on the one is inner node of the other
	- <mark style="background: #BBFABBA6;">all nodes can send and receive</mark>
	- ![[Pasted image 20250327122233.png | 300]]
	- optimal time
- ESBT Broadcast
	- Edge Disjoint Binomial Trees
	- Structure PEs as a Hypercube ($p = 2^d$)
		- decompose into $d$ ESBTs
	- PE $0$ distributes packets to the roots, from there its a binomial tree broadcast
	- In step $i$ there is communication is dimension $i\ mod\ d$
	- optimal with $n \beta + d \alpha + 2 \sqrt{np \alpha \beta}$
## Sorting

- Vl 4 ff
- Fast Inefficient Ranking
	- Like the maximum, broadcast your element to everyone, calc $A_i \geq A_j$ and reduce to get the number of smaller elements ($O(\alpha\ log(p))$)
	- Also possible to do this with Brents Principle
		- ![[Pasted image 20250327141915.png]]
		- $O(\alpha\ log(p) + \beta \frac{n}{\sqrt{p}} + \frac{n}{p}log(\frac{n}{p}))$ 
			- $\beta \frac{n}{\sqrt{p}}$ through the bigger messages; because only rows or columns are sent, the length has the square root
			- $\frac{n}{p}log(\frac{n}{p})$ because of the local sorting
		- Local ranking with the two sorted arrays $r$ and $c$ can be done in $O(|r| + |c|)$
		- <mark style="background: #BBFABBA6;">the fastest for low counts of elements per PE</mark>
- Quicksort
	1. Pick a pivot (choose PE random weighted by the local element count, choose element random)
	2. partition locally into small elements $a$ and big elements $b$
	3. Calculate number of small and big elements $n_a, n_b$ through 2 reductions
	4. $k' = \frac{n_a}{n_a + n_b}$ PEs should work on small elements, round $k'$ smart to minimize load inbalance
	5. send $a$ and $b$ to the right PEs, split them up if needed
	6. Keep on working on the small or the big elements, depending if the own index is smaller or bigger then $k$
	- $\frac{n}{p} (log\ n+\beta log\ p) + \alpha log^2 \ p$
	- <mark style="background: #FF5582A6;">Its bad that the data is sent log times</mark>
	- <mark style="background: #BBFABBA6;">local work is theoretical optimal</mark>
- Sample Sort
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
- Multiway merging
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
- CRCW Theoretical Sampling Sort
	1. Sampling and splitter selection
	2. Allocate buckets twice as big as expected size
	3. write to random position in the buckets
	4. compactify with prefix sums
	5. Recursion
	- <mark style="background: #BBFABBA6;">theoraticaly achieves logarithmic time</mark>

## Präfix Sum

- Linear Pipeline like in Broadcasting
- Hypercube
	- Always communicate 
## Gossiping

- VL 7
- Hypercube Algorithm

## h-Relation

- VL 8
- Für Nachrichten gleicher Länge
	- Hypercube Algorithm
		- Gut für kurze Nachrichten
	- 1-Factor Algorithm
		- Gut für lange Nachrichten
- Für Nachrichten unterschiedlicher Länge
	- Ostrich Algorithm
		- Scheduling über Bipartite Multigraphen
	- Coloring based Algos
	- 2 Phase Algorithm
	- Non-Preemtive

## Priority Queue und Branch and Bound

- VL 8 und 9 und 13
- Effizientes Bulk insert und bulk delete min
- Selection Algorithm
- Communication Efficient Parallel Queues
- Shared Memory Parallel Queues
- Relaxed Multiqueues
	- Buffering
	- Stickyness

## List Ranking

- Vl 13
- Pointer Doubeling
	- Braucht p = n um gut zu sein 
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