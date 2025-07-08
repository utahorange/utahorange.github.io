---
layout: post
title: Playing with Threads for Matmults Part I
date: 2025-4-1 15:00:00
description:
tags: concurrency
categories: 
thumbnail: 
---
For a side project, I've been digging into C++ concurrency primitives. Previously, I finished reading OSTEP and found thread synchronization unintuitive, but very interesting.

To learn more about how to use `std::thread`, I decided to do a performance comparison of threaded vs unthreaded matmult. Matmult (or matrix multiplication) is a very big thing nowadays and is an obviously parallelizable task. A thread to compute dot product can be dispatched for each element of the resultant matrix, since the elements of the result are not dependent on each other.

That's really what makes ML models feasible: GPU/TPU's now have the ability to really parallelize their matmults for training/inference. As one of my ECE professors recently said, the AI boom was fueled by hardware innovations that saw the Scaling Law allow us to actually have good results with deep neural networks.

## quick theory overview

I'll quickly review how to multiply two matrices together to see where multi-threading comes in. The naive way to do matmults is to simply do three for-loops: two for-loops to go through every result element of the result matrix and one for-loop to go through the dot product computation row-wise on matrix A and column-wise on matrix B for the product $$AB=C$$.

To multiply two matrices together requires the number of **columns** of the first matrix to match the number of **rows** of the second. I do that check with C++'s `std::cassert` library.

```cpp
```

## my thought process going in

Having been inspired by videos like [LaurieWired's Santa concurrency problem](https://www.youtube.com/watch?v=zwUzulwiDpI&ab_channel=LaurieWired), I thought naively 


## trolling
"That's weird", I remarked as I saw the multi-threading implementation often taking as much as a factor 10 times longer than the unthreaded version.

## conclusions
Turns out, threading is not as OP as I thought. Naively applying optimizations like threading doesn't necessarily translate to real performance benefits. In hindsight, I probably should've seen this one coming, since this was an often-stated theme of OSTEP and software dev articles I've read. "Premature optimization is the root of all evil" or something.

A good summary of the possible performance problems with naive multithreading can be found in [this StackOverflow post](https://stackoverflow.com/questions/50082047/multi-threaded-matrix-multiplication-performance-issue).

In reality, no one's hand-coding implementations of matmult or whatnot by hand nowadays. Just use Python with JIT or Numba or something says very pragmatic ML researchers. And the naive triple for-loop matmult algorithm isn't even the most efficient (in terms of Big O) algorithm around. With some [mysterious linear algebra](https://people.csail.mit.edu/virgi/matrixmult-f.pdf), you can get down to $$O(n^{2.373})$$ instead of $$O(n^3)$$.

My code for the threaded matmult comparisons can be found [here](https://github.com/utahorange/matmult-testing) as well as some other concurrency practice programs I was playing with.