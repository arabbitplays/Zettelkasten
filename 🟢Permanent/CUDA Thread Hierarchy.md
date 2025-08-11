# CUDA Thread Hierarchy

## Introduction

- Threads should be structured in a way, that programmers can specify their programs in a way that it can execute independent of the physical core count
- the concepts are introduced combined with how they are exposed in CUDA C++

- a <mark style="background: #FFB86CA6;">block</mark> is a 3-dimensional collection of threads, executing in parallel
	- 3-dimensions allow it to naturally work within domains like images or volumes
	- the intern variable `threadIdx` gives the index of a thread as a vector
	- the intern variable `blockDim` gives the dimensions of one block
- blocks are structured in a 3D grid of blocks
	- the intern variable `blockIdx` gives the index of a block in the grid

```c++
//Kernel definition
__global__ void MatAdd(float a[N][N], float b[N][N], float c[N][N]) {
	int i = blockIdx.x * blockDim.x + threadIdx.x;
	int j = blockIdx.y * blockDim.y + threadIdx.y;
	if (i < N && j < N) {
		c[i][j] = a[i][j] + b[i][j];
	}
}

void main() {
	dim3 threads_per_block(16, 16);
	dim3 num_blocks(N / threads_per_block.x, N / threads_per_block.y);
	MatAdd<<<num_blocks, threads_per_block>>>(a, b, c);
}
```

- blocks should be able to execute independently
	- it is not known in which sequence they execute and if the execute in parallel
- threads in a block can cooperate
	- they all have access to a low latency shared memory
	- `__syncthreads()` defines a barrier in the kernel, synchronizing all threads of the block

---

Origin: [CUDA C Programming Guide](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html)
References: 
Tags: 
Created: 29.07.2025

