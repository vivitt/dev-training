# The max number of flags

In this exercise, an array of numbers represents the view of a mountain range.
A peak is an element that is greater than its immediate neighbors.
You can place flags on the peaks, but the distance between any two flags must be equal or greater than X,  where X is the total number of flags being placed.
The goal is to determine the maximum number of flags that can be set on the peaks following this rule.

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
    let flags = Math.floor(Math.sqrt(peaks[p-1]))
    let count = 1
    let first = peaks[0]
    for(let i = 1; i < p; i++) {
        if(peaks[i] - first >= flags) {
            count++
            first = peaks[i]
        }
    }
    return count
}
```
