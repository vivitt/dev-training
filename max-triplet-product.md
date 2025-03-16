# Find the Maximum Triplet Product

The goal of this exercise is to find the maximal product of any triplet in a non-empty array of integers.

```
function solution(A) {
    const sorted = A.sort((a, b) => b-a)
    return sorted[0] * sorted[1] * sorted[2]
}
```
