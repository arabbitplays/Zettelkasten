# Message Passing Interface (MPI)
- siehe auch [[🪐Areas/✈️Travel/🅾️Programming/Setup#MPI]]

## Introduction

- General C/C++ interface for [[Inter Process Communication]]
- programs are written as [[Single Program Multiple Data principle | SPMD]]
## Initialization

- Processes communicate over <mark style="background: #FFB86CA6;">Communicators</mark>
	- Standard Communicator is MPI_COMM_WORLD

```C
#include<stdio.h> 
#include<mpi.h> 
int main(int argc, char** args) { 
	int size; // Anzahl der Prozesse die mit MPI laufen
	int myrank; // ID des aktuellen Prozesses
	MPI_Init(&argc, &args); 
	MPI_Comm_size(MPI_COMM_WORLD, &size); 
	MPI_Comm_rank(MPI_COMM_WORLD, &myrank); 
	printf("Hello world, I have rank %d out of%d.\n", myrank, size); 
	MPI_Finalize();
	return 0; 
}
```
```bash
mpicc hello.c // calls c compiler intern
mpirun -np 3 a.out // run programm with 3 processes
```

## Point-to-Point Message Passing

```C
// Block until all processes have arrived here.
int MPI_Barrier(MPI_Comm comm) 

// Asynchronous and blocking point-to-point communication.
// Blocks until sending has STARTED!
// dest is the ID of the recipient, tag is only an optional label
int MPI_Send(void* buffer, int count, MPI_Datatype datatype, int dest, int tag, MPI_Comm comm)
// blocks until receiving has started
// Receive has wildcard with MPI_ANY_SOURCE, tag has wildcard MPI_ANY_TAG, status contains the actual sender and tag
int MPI_Recv(void* buffer, int count, MPI_Datatype datatype, int source, int tag, MPI_Comm comm, MPI_Status* status)
```

- Communication Modes
	- Synchronous (`MPI_Ssend`)
		- No buffer, but synchronization
	- Buffered (`MPI_Bsend`)
		- Explicit buffering, but no synchronization
	- Standard 
		- Not clearly defined
- (Non-)blocking Communication
	- Orthogonal to the modes
	- Blocking
		- Return only when operation is complete
	- Non-blocking (MPI_Isend (has `MPI_Request*` as parameter))
		- Direct return
	- No certainty when buffers can be reused
		- Tests after completion with `MPI_Test(MPI_Request* r, int* flag, MPI_Status* s)` (non-blocking) or `MPI_Wait(MPI_Request* r, MPI_Status* s)` (blocking)

## Global Collective Operations

![[Pasted image 20240124140438.png]]


---

Origin: 
References: 
Tags: 
Created: 12.08.2025