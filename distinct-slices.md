# Count Distinct Slices

Given an integer M and a non-empty array A of non-negative integers, where each element is less than or equal to M.
The goal in this task is to count the number of different slices.

The solution must return 1,000,000,000 if the number of different slices equals or exceeds this value.

```
function solution(M, A) {
    let distinctSLices = 1
    let right = 0
    const count = Array.from({length: M + 1}).fill(0)
    count[A[right]] = 1

    let currentElements = 1
    let left = 0
    while(left <= A.length && right <= A.length) {
        
        if(count[A[right+1]] === 0) {
            right++
            currentElements++
            count[A[right]] = 1
            distinctSLices += currentElements
        } else {
            count[A[left]] = 0
            currentElements--
            left++
        }

        if(distinctSLices >= 1000000000) return 1000000000
    }

    return distinctSLices
}
```
