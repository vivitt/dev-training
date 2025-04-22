# Array Peaks

Given a non-empty array, the goal of this task is to find the maximum number of blocks into which the array can be divided, with each block containing at least one peak.

```
function solution(A) {
    const l = A.length
    if(l <= 1) return 0
    const peaks = []
    for(let i = 1; i < l-1 ; i++) {
        if(A[i-1] < A[i] && A[i] > A[i+1]) {
            peaks.push(i)
        }
    }
    
    const numberOfPeaks = peaks.length
    if(numberOfPeaks <= 1) return numberOfPeaks

    const factors = []

    let i = 2
    while(i <= numberOfPeaks) {
        if(l % i === 0) {
            factors.push(i)   
        }
        i++
    }
    if(!factors[0])return 1

    let factorIndex = factors.length-1
    let j = 0
    let elements = l / factors[factorIndex]
   
    while(j < numberOfPeaks) {
        if(factorIndex < 0)return 0
        if(peaks[j] < elements * (j+1)) {
            j++
        } else {
            factorIndex--
            elements = l / factors[factorIndex]
        }
    }

    return factors[factorIndex]
}
```
