# Find the Minimal Absolute Sum of Two Array Values

The goal is to find the minimal absolute sum of two values in a non-empty array A.

```
function solution(A) {
    const L = A.length

    const sorted = A.sort((a, b) => a - b)

    let left = 0
    let right = 0

    let minAbs = Math.abs(sorted[left] + sorted[right])

    while(left < L){
        if(sorted[left] < 0 && sorted[right+1]) {
            right++
        } else {
            left++
            right = left
        }
        
        if(Math.abs(sorted[left] + sorted[right]) < minAbs) {
            minAbs = Math.abs(sorted[left] + sorted[right])
        }
        
    }
    return minAbs
}
```

An optimized version uses the two-pointer technique, starting with one pointer at the beginning of the array (left) and the other at the end (right).
The initial minimal sum is set to twice the smallest absolute value in the array.

Iterate while the left pointer is less than or equal to the right pointer, calculating the sum at each step.
Update the minimal sum when a smaller absolute value is found. Then, 
- if the sum is negative, move the left pointer forward, 
- if the sum is positive, move the right pointer backward, 
- if the sum is zero, return 0 as it's not possible to achieve a smaller value.

```
function solution(A) {
    const sorted = A.sort((a, b) => a-b)

    let left = 0

    let right = A.length - 1

    let minAbs = Math.abs(sorted[0] + sorted[0])

    while(left <= right) {
        const sum = sorted[left] + sorted[right]

        minAbs = Math.min(Math.abs(sum), minAbs)

        if(sum < 0) {
            left++
        } else if (sum > 0) {
            right--
        } else {
            return 0
        }
    }
    return minAbs
}
```
