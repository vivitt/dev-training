# Find the max double slice sum

Given a non-empty array A containing N elements, a double slice is defined by a triplet of indices (P, Q, R) such that 0 ≤ P < Q < R < N.

The sum of a double slice is calculated as:
A[P+1] + A[P+2] + ... + A[Q−1] + A[Q+1] + A[Q+2] + ... + A[R−1]
(Note that A[Q] is excluded.)

The goal of this exercise is to find the maximum sum of any double slice in the array.

```
function solution(A) {
    const l = A.length
    if(l <= 3) return 0
    let max_end = Array.from(A).fill(0)
    let max_start = Array.from(A).fill(0)

    for (let i = 1; i < l-1; i++){
        max_end[i] = Math.max(0, max_end[i - 1] + A[i])
    }
    
    for (let i = l-2; i > -1; i--) {
        max_start[i] = Math.max(0, max_start[i + 1] + A[i])
    }
        
    max_double_slice = 0

    for (let i= 1; i < l -1; i++) { 
        max_double_slice = Math.max(max_double_slice, max_end[i - 1] + max_start[i + 1])}

    return max_double_slice
}
```
