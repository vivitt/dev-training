# Triangle

The goal of this exercise is to determine if a given array contains any triplet that forms a triangular triplet.
The function should return 1 if such a triplet exists and 0 otherwise.

```
function solution(A) {

    const l = A.length
    const sorted = A.sort((a, b) => a - b)

    for(let i = 0; i < l-2; i++ ) {
        if(sorted[i] + sorted[i+1] > sorted[i+2]) return 1
    }
    return 0

}
```
