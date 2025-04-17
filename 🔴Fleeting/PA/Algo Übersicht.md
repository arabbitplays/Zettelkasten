

## Sorting



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
	- while $R(Q(i)) \neq 0$ do $R(i) += R(Q(i))$ and $Q(i) = Q(Q(i))$
	- <mark style="background: #FF5582A6;">Very much work</mark> ($n\ log(n))$) -> time $O(log(n))$
	- <mark style="background: #BBFABBA6;">used as a base case for other algos</mark>
- Independend set removal
	- Inpedend Set: Weder pre noch successor ist schon im set
	- Remove independend set from the instance
		- add the $R$ of a removed node to the successor
	- when reinserting, the $R$ value is one smaller then the successor
	- Finding an independend set
		- flip a coin $c_i \in \{0, 1\}$ for every element, if $c_i = 1$ and both pre- and successor have $0$, add $i$ to the set
		- repeat until $|I| = n / 5$
		- $O(n/p)$
	- New index for the recursion is just an ascending numbering for the elements not in the set
	- <mark style="background: #D2B3FFA6;">linear work with bad constant factors</mark>
	- ![[Pasted image 20250330103909.png| 400]]
- <mark style="background: #FFB86CA6;">Ruling Set List Removal</mark>
	- Pick $O(p\ log(p))$ samples, solve the instance until the next sample is found
	- use work stealing load balancing
	- concat the subresults with a prefix sum
	- $O(n/p + log(p)) + time\ for\ subproblem$ 
	- <mark style="background: #BBFABBA6;">optimal with optimal base case algo</mark>
	- ![[Pasted image 20250330105135.png | 400]]

## MST

- [[Minimum Spanning Trees (MST)]]
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