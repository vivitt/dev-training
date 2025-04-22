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
    const p = peaks.length
    if (p <= 1) return p

    const factors = []

    let i = 2
    while(i <= p) {
        if(l % i === 0) {
            factors.push(i)   
        }
        i++
    }

    for(let i = factors.length-1; i >= 0; i--) {
        const elements = l/factors[i]
        
        if(peaks[0] < elements) {
            let count = 1
            for(let j = 1; j < p; j++) {
                if(peaks[j] >= elements * count) {
                    count++
                }
                if(count === factors[i]) return factors[i]
            }
        }   
    }
    return 1
}
```
