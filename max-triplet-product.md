# Find the Maximum Triplet Product

The goal of this exercise is to find the maximal product of any triplet in a non-empty array of integers.

```
function solution(A) {
    const triplets = []

    for(let i = 0; i < A.length - 2; i++) {
        for(let j = i+1; j<A.length -1; j++) {
            triplets.push([A[i] * A[j] *A[j+1]] )
        }
    }

    return Math.max(...triplets)
}
```
