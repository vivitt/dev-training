# Find the Maximum Triplet Product

The goal of this exercise is to find the maximal product of any triplet in a non-empty array of integers.

```
function solution(A) {
    const sorted = A.sorted((a, b) => b - a)
    const productOne = sorted[0] * sorted[1] * sorted[2]
    const productTwo = sorted[A.length-1] * sorted[A.length-2] * sorted[0]

    return Math.max(productOne, productTwo)
}

```
