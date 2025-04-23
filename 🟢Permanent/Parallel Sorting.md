# Parallel Sorting


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

---

Origin: Parallele Algorithmen Vorlesung
References:  [[Parallel Computing Index]], [[Parallel Machinemodels]]
Tags: 
Created: 17.04.2025

