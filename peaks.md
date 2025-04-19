# Array Peaks

Given a non-empty array, the goal of this task is to find the maximum number of blocks into which the array can be divided, with each block containing at least one peak.

```
function solution(A) {
    const l = A.length
    const peaks = []

    for(let i = 1; i < l-1; i++) {
        if(A[i-1] < A[i] && A[i] > A[i+1]) {
            peaks.push(i)
        }
    }
    let p = peaks.length
    if(p <= 1) return p

    return Math.floor(peaks[p-1] / p)
}
```
