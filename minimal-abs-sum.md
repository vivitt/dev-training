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

```
function solution(A) {
    const l = A.length

    const maxSum = A.reduce((acc, el) => acc + el, 0)
    if(maxSum === 0) return 0
    const dpSize = Math.abs(maxSum) + 1

    let dp = Array.from({length: dpSize}).fill(false)
    dp[dpSize-1] = true

    for(let num of A) {
        const nextDp = [...dp]
        for(let i = 0; i < dpSize; i++) {
           if(dp[i]) {
               if(i === 0) return 0
               if(maxSum < 0) {
                   if(Math.abs(-i - 2* num) < dpSize && (-i - num * 2 <= 0)) {
                       nextDp[Math.abs(-i - 2* num)] = true
                   }
               } else {
                   if(Math.abs(i - 2 * num) < dpSize && i - 2 * num >= 0) {
                       nextDp[Math.abs(i - 2* num) ] = true
                   }
               } 
               
           }
        }
        dp = nextDp
    }
    for(let i = 0; i < dpSize; i++) {
        if (dp[i]) return i;
    }
}
```
