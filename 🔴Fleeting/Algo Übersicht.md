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