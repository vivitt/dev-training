# Array Peaks

Given a non-empty array, the goal of this task is to find the maximum number of blocks into which the array can be divided, with each block containing at least one peak.

```
function solution(A) {
       const l = A.length
    if(l <= 1) return 0

    let i = 2
    let factors = []

    while(i*i < l) {
        if(l % i === 0) {
            factors.push(i)   
        }
        i++
    }
    if(factors.length === 0) return 0
    const peaks = []

    for(let i = 1; i < l-1; i++) {
        if(A[i-1] < A[i] && A[i] > A[i+1]) {
            peaks.push(i)
        }
    }

    const totalPeaks = peaks.length
    if(totalPeaks <= 1) return 0

    let currentFactor = factors.length-1
    let currentEl = 0

    let j = 0

    while(currentEl < l) {
         const els = l / factors[currentFactor]
        if(peaks[j] < currentEl+els) {
            currentEl+= els
            j++
        } else {
            if(currentFactor === 0) return 0
            currentFactor--
            currentEl = 0
            j = 0  
        }
    }
    return factors[currentFactor]
}
```
