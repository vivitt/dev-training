# Nailing Planks

In this exercise, the input consists of two non-empty arrays of N integers, A and B, representing the starting and ending positions of planks.
There is also a third array of integers, C, representing the positions of nails. A plank is considered nailed if there exists an element C[i] such that `A[k] ≤ C[i] ≤ B[k]`.
The goal is to find the minimum number of nails, used in order, that are enough to nail all the planks represented by A and B.

```
function solution(A, B, C) {
    let min = 1

    let max = C.length

    let nails = -1


    while(min <= max) {

        const nailed = new Array(A.length).fill(false);

        const mid = Math.floor((min + max) / 2);

        for (let i = 0; i < A.length; i++) {
            for (let j = 0; j < mid; j++) {
                if (A[i] <= C[j] && C[j] <= B[i]) {
                    nailed[i] = true;
                    break;
                }
            }
        }

        if(!nailed.includes(false)) {
            nails = mid;
            max = mid - 1;
        } else {
            min = mid + 1;
        }
    }
    return nails
}
```
