# Count the Non Overlapping Segments

This task begins with two arrays of integers, representing the starting and ending points of segments, respectively.
The goal is to find the maximum number of non-overlapping segments.
Two segments are considered overlapping if A[i] ≤ A[j] ≤ B[i] or A[j] ≤ A[i] ≤ B[j].

The problem can be solved using a **greedy algorithm**. This technique consists of making the optimal choice at each step in order to reach the overall optimal solution.
Greedy algorithms are not suitable for all problems; in some cases, functional programming techniques or brute-force approaches may be necessary.
When a greedy algorithm is applicable, it is usually the most efficient option and runs faster than other methods.

```
function solution(A, B) {
    const L = A.length
    if(L <= 1) return L
    let last = 0
    let nonOverlapping = 0
    for(let i = 0; i < L; i++) {
        if(A[i] > last) {
            nonOverlapping++
            last = B[i]
        }
    }

    return nonOverlapping
}
```
