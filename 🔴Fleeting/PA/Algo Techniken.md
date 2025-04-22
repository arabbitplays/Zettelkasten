
## Parallelization of Recursion

- bad for distributed memory
- load balancing needed
- very limited speedup

## Dart Throwing

- in a CRCW PRAM: allocate big buckets and throw elements into random position -> chance for congestion is low if the buckets are big enough
- Example is a variant of sample sort, where the buckets are twice as big as expected with high probability

## Pointer Doubeling

- 2 Pointer durch einen ersetzen und dabei Dinge machen 
- example is some alogs in list ranking