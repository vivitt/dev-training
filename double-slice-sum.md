# Find the max double slice sum

Within a non empty array A containing N elements, a double slice is a triplet of elements such that 0 <= P < Q < R < N.
The sum of those elements equals to A[P+1] + A[P+2] + ... + A[Q-1] + A[Q+1] + A[Q+2] + ... + A[R-1]
The goal in this exercise is to find the maximal double slice sum for a given array.

```
function solution(A) {
    const l = A.length
    if(l <= 3) return 0

    const prefix = Array.from(A).fill(0)
    
    let max_end = 0
    let max_slice = 0

    let minEl = A[1]
    let hasNegativeElements = false
    for(let i = 1; i < l-1; i++) {
        prefix[i] =  prefix[i-1] + A[i] 
        max_end += A[i]
        if(prefix[i] < prefix[i-1]) {
            hasNegativeElements = true
            max_end -= A[i]
        } else {
            minEl = A[i] < minEl ?A[i] :minEl
        }

        max_slice = Math.max(max_end, max_slice)
        
    }

    return hasNegativeElements ?max_slice :max_slice-minEl
}
```
