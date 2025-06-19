# Tie Ropes

Given an array A representing the lengths of ropes and an integer K, the goal of this problem is to find the number of ropes that can be tied together to form lengths greater than or equal to K.
Two ropes can be tied together if they are adjacent in the array (ropes `i` and `i + 1`).
Once ropes are tied, the resulting rope can be tied again with the next adjacent one.

```
function solution(K, A) {
    const L = A.length

    let left = 0
    let right = L - 1

    let currentRope = A[left]
    let ropes = 0
    while(left <= right) {
        if(currentRope >= K) {
            ropes++
            currentRope = 0
        }
        left++
        currentRope += A[left]
    }
    return ropes
}
```
