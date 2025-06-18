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
