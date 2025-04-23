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

    if(p <= 1) return p

    let i = 2
    const factors = []

    while(i <= p) {
        if(l % i === 0) {
            factors.push(i)
        }
        i++
    }

    if(!factors[0])return 1

    const f = factors.length
    
    let j = f-1
    while(j > -1) {
        const elements = l/factors[j]
        if(peaks[0] >= elements) j--
        let count = 1
        for(let h = 1; h < p; h++) {
            if(Math.floor(peaks[h] / elements) === count) {
                count++
            } 
            else if(Math.floor(peaks[h] / elements) > count) {
                j--
            }
            
            if(count === factors[j]) return factors[j]
        }
        
    }
    return 1

}
```
