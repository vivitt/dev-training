# Count Non Divisors

Given a non-empty array of integers, the task in this exercise is to count how many elements in the array are non-divisors for each value.

```
function solution(A) {
    const l = A.length

    const sorted = [...new Set(A)].sort((a, b) => a - b)

    const s = sorted.length

    const max = sorted[s-1]
    const countOccurrences = Array.from({length: max+1}).fill(0)

    for(let i = 0; i < l; i++) {
        countOccurrences[A[i]]++
    }

    const countNonDivisors = Array.from({length: max+1}).fill(0)

    let totalElements = l

    for(let i = 0; i < s; i++) {

        totalElements -= countOccurrences[sorted[i]]
        
        countNonDivisors[sorted[i]] += totalElements
        for(let j = 0; j < i; j++) {
            if(sorted[i] % sorted[j] !== 0) {
                countNonDivisors[sorted[i]] += countOccurrences[sorted[j]]
            }
        }
    }

    const result = []

    for(let i = 0; i < l ; i ++) {
        result[i] = countNonDivisors[A[i]]
    }

    return result
}
```
