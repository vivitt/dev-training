# Count Non Divisors

Given a non-empty array of integers, the task in this exercise is to count how many elements in the array are non-divisors for each value.

```
function solution(A) {
    const l = A.length;
    const sorted = [...new Set(A)].sort((a, b) => a - b);
    const max = sorted[sorted.length-1];

    const count = Array(max + 1).fill(0);

    for(let i = 0; i < l; i++) {
        count[A[i]]++;
    }

    const isPrime = Array(max + 1).fill(true);

    isPrime[0] = isPrime[1] = false;

    const nonDivisors = Array(max + 1).fill(l - count[1]);

    for(let i = 2; i <= max; i++) {
        for(let j = i+i; j <= max; j += i) {
            if(count[j] !== 0) {
                nonDivisors[j] -= count[i];
            }
        }
        nonDivisors[i]-=count[i];
    }
        
    const result = [];

    for(let i = 0; i < l; i++) {
        result[i] = nonDivisors[A[i]];
    }

    return result;
}
```
