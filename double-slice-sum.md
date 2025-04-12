# Find the max double slice sum

Given a non-empty array A containing N elements, a double slice is defined by a triplet of indices (P, Q, R) such that 0 ≤ P < Q < R < N.

The sum of a double slice is calculated as:
A[P+1] + A[P+2] + ... + A[Q−1] + A[Q+1] + A[Q+2] + ... + A[R−1]
(Note that A[Q] is excluded.)

The goal of this exercise is to find the maximum sum of any double slice in the array.

```
function solution(A) {
    const l = A.length

    const maxEnd = Array.from(A).fill(0)
    const maxStart = Array.from(A).fill(0)

    for(let i = 1; i < l-1; i++) {
        maxEnd[i] = Math.max(0, maxEnd[i-1] + A[i])
    }

    for(let i = l-2; i > -1; i--) {
        maxStart[i] = Math.max(0, maxStart[i+1] + A[i])
    }

    let maxDouble = maxEnd[0] + maxStart[2]

    for(let i = 2; i < l-1; i++) {
        maxDouble = Math.max(maxDouble, maxEnd[i-1] + maxStart[i+1] )
    }
    return maxDouble
}
```
