# Count Non Divisors

Given a non-empty array of integers, the task in this exercise is to count how many elements in the array are non-divisors for each value.

```
function solution(A) {
    const l = A.length

    const sorted = [...new Set(A)].sort((a, b) => a - b)

    const max = sorted[sorted.length -1]
    const count = Array.from({length:  max+1}).fill(0)

    for(let i = 0; i < l; i++) {
        count[A[i]]++
    }

    const nonDivisors = Array.from(count).fill(0)
    for(let i = 0; i < sorted.length; i++) {
        for(let j = 2; j <= max; j++) {
            if(count[j] !== 0 && sorted[i] % j !== 0) {
                nonDivisors[sorted[i]] += count[j]
            }
        }
        
    }
    const result = Array.from(A).fill(0)

    for(let i = 0; i < l ; i++) {
        result[i] = nonDivisors[A[i]]
    }
    return result
}
```
