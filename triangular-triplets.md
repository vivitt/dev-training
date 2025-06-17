# Count Triangular Triplets

The goal in this task is to count the number of triagular triplets within an array A of N integers. 

A triplet P, Q, R is triangular if `0 ≤ P < Q < R < N` and:
* A[P] + A[Q] > A[R]
* A[Q] + A[R] > A[P]
* A[R] + A[P] > A[Q]

The first approach iterates over all possible triplet combinations:

```
function solution(A) {
    const L = A.length

    let count = 0
    
    for(let p = 0; p < L-2; p++) {
        let q = p + 1
        let r = q + 1
        while(q < L - 1 && r < L) {
            if(A[p] + A[q] > A[r] && A[q] + A[r] > A[p] && A[r] + A[p] > A[q]) {
                count++
            }
            if(r < L-1) {
                r++
            } else {
                q++
                r= q + 1
            }
        }
    }
    return count
}
```

But this solution can be optimized using the caterpillar method, which reduces the time complexity to O(N**2):

```
function solution(A) {
    const L = A.length

    const sorted = A.sort((a, b) => a - b)

    let count = 0

    for(let p = 0; p < L-2; p++) {
        let r = p + 2
        for(let q = p+1; q < L-1; q++) {
            while (r < L && sorted[p] + sorted[q] > sorted[r]) {
                r += 1
                
            }
            count += r - q - 1
            
        }
    }

    return count
}
```
