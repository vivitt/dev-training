# Find the Maximum Slice Value

Given a non-empty array, the task in this exercise is to find a slice with the maximum possible sum.

```
function solution(A) {
    const l = A.length
    let max_end = 0
    let max_slice = A.reduce((acc, el) => acc + el)

    for(let i = 0; i < l; i++) {
        max_end = Math.max(A[i], max_end+A[i])
        max_slice = Math.max(max_end, max_slice)
    }

    return max_slice
}
```
