# Find the Maximum Triplet Product

The goal of this exercise is to find the maximal product of any triplet in a non-empty array of integers.

```
function solution(A) {
    
    let P = 0
    let Q = 1
    let R = 2

    let product = (A[P] * A[Q]) * A[R]
    while(P < A.length - 2) {
        const current = (A[P] * A[Q]) * A[R]
        if(current > product) {
            product = current
        }
        if(R === A.length-1) {
            P++
            Q = P + 1
            R = Q + 1
        } else {
            Q++
            R++
        }
    }
    return product

}

```
