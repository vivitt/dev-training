# Find the Maximum Slice Value

Given a non-empty array, the task in this exercise is to find a slice with the maximum possible sum.

```
function solution(A) {
    // Implement your solution here
    const l = A.length

    let max_end = A[0]
    let max_slice = A[0]

    for(let i = 1; i < l; i++) {
        max_end = Math.max(0, max_end + A[i])
        max_slice = Math.max(max_end, max_slice)
    }
    return max_slice
}
```
