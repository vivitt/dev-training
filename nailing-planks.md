# Nailing Planks

In this exercise, the input consists of two non-empty arrays of N integers, A and B, representing the starting and ending positions of planks.
There is also a third array of integers C representing positions of nails. A plank is considered nailed if there exists an element C[i] such that `A[k] ≤ C[i] ≤ B[k]`.
The goal is to find the minimum number of nails, that used in order are enough to nail all the planks represented by A and B.
If it is not possible to nail all the planks, the function must return -1.

```
function solution(A, B, C) {
    let min = 1
    let max = C.length
    let nails = -1
    while(min <= max) {
        const mid = Math.floor((min + max) / 2)
        const nailed = new Set()

        for(let i = 0; i < A.length; i++) {
            for(let j = 0 ; j < mid; j++) {
                if(A[i] <= C[j] && C[j] <= B[i]) {
                    nailed.add(i)
                    break;
                }
            }
        }

        if(nailed.size === A.length) {
            nails = mid
            max = mid - 1
        } else {
            min = mid + 1
        }
    }
    return nails
}
```
