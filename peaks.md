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

    const factors = []

    for(let i = p; i > 1; i--) {
        if(l%i===0){
            factors.push(i)
        }
    }

    if(factors.length < 1)return 1

    let factorIndex = 0
    let blocks = factors[factorIndex]
    let elements = 0
    let currentPeak = 0
    while(currentPeak < p && elements < l) {
        if(peaks[currentPeak] >= elements && peaks[currentPeak] < (elements + l / blocks)) {
            elements += l / blocks
        } else if(peaks[currentPeak] > (elements + l / blocks)) {
            factorIndex++
            if(factorIndex === factors.length)return 1
            blocks = factors[factorIndex]
            elements = 0
            currentPeak = 0
        }
        currentPeak++
    }
    return blocks
}
```
