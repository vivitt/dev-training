# Minimal Absolute Sum

Given an integer array A and an array S of the same length with values from the set {1, -1}, you need to find the minimal possible value of `val(A, S)`, where:

`val(A, S) = |sum{ A[i] * S[i] for i = 0..N−1 }|`

```
function solution(A) {
    const l = A.length
    if(l === 0) return 0
    if(l === 1) return Math.abs(A[0])

    const possibles = new Set()

    possibles.add(Math.abs(A[0]))

    for(let i = 1; i < l; i++) {
        const possibleSums = new Set()
        for(let j = 0; j < possibles.size; j++) {
            possibleSums.add(Math.abs([...possibles][j] + A[i]))
            
            possibleSums.add(Math.abs([...possibles][j] - A[i]))
             
        }
        
        possibles.clear();
        for (const val of possibleSums) {
            possibles.add(val);
        }    
    }
    return Math.min(...[...possibles])
}
```
