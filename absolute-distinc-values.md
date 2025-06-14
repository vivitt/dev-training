# Count the Absolute Distinct Values

A non-empty array of integers is given, and the task is to count the number of distinct absolute values present in the array.
The solution can be optimized using the *caterpillar method*.
This technique consists of simulating the behavior of a caterpillar, tracking the initial and last values in the array that meet a certain condition.
With each iteration, either the left or right end moves one position forward, depending on whether the condition is still met.

```
function solution(A) {

    const sorted = A.map((el) => Math.abs(el)).sort((a, b) => a - b)
    let left = sorted[0]
    let right = left

    let count = 1
    for(let i = 1; i < A.length; i++) {
        if(sorted[i] !== right) {
            right = sorted[i]
            count++
        } else {
            left = A[i]
        }
    }

    return count
}
```
