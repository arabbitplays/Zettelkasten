# Very Long Instruction Word

## Introduction

- the base idea is to let the compiler do the parallelization by generating complex instructions
- the instructions consist of multiple parts, each following RISC operations and each instructing one execution unit
- mainly used in embedded systems

## Compilation Process for VLIW Architectures

- compiler does the analysis of data and control flow
- unroll loops to overlap the iterations
- schedule different operations to different execution units -> encoded in the long instruction

---

Origin: 
References: 
Tags: 
Created: 11.08.2025

