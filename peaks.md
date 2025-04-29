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
    const f = factors.length

    if(f < 1)return 1


    for(let i = 0; i < f; i++) {
        const blocks = factors[i]
        let elements = 0
        for(let j = 0; j < p; j++) {
            if(peaks[j] >= elements && peaks[j] < elements + l / blocks) {
                elements += l / blocks
            }
            if(elements === l) return blocks
        }
    }
    return 1
}
```
