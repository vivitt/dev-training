# Find the Maximum Triplet Product

The goal of this exercise is to find the maximal product of any triplet in a non-empty array of integers.

```
function solution(A) {
    A.sort((a,b) => b-a)
    return A[0] * A[1] * A[2]
}
```
