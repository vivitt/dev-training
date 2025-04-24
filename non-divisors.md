# Count Non Divisors

Given a non-empty array of integers, the task in this exercise is to count how many elements in the array are non-divisors for each value.

```
function solution(A) {
    const l = A.length
    const result = Array.from(A).fill(0)

    const sorted = [...new Set(A)].sort((a,b) => b - a)
    const maxEl = sorted[0]

    const countNonDivisors = Array.from({length: maxEl+1}).fill(0)

    const countElements = Array.from({length: maxEl+1}).fill(0)

    for(let i = 0; i < l; i++) {
        countElements[A[i]]++
    }

    for(let i = 0; i < sorted.length; i++) {
        for(let j = 0; j < sorted.length; j++) {
            if(j < i) {
                countNonDivisors[sorted[i]] += countElements[sorted[j]]
            }
            
            if(j > i && sorted[i] % sorted[j] !== 0) {
                countNonDivisors[sorted[i]] += countElements[sorted[j]]
            }
        }    
    }

    for(let i = 0; i < l; i++) {
        result[i] = countNonDivisors[A[i]]
    }
    return result
}
```
