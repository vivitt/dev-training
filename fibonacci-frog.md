# Fibonacci Frog

A small frog wants to cross the river. Starting from position -1, the frog must reach the other side at position N.
The frog can only jump onto leaves, represented by an array A, where each 0 is water and each 1 is a leaf.

The frog can jump any distance F(K), where F(K) is the K-th Fibonacci number.
The Fibonacci sequence is defined as:
```
F(0) = 0
F(1) = 1
F(M) = F(M-1) + F(M-2), if M >= 2
```

The solution must return the minimum number of jumps the frog must take to reach the other side, or -1 if it is not possible to cross.
