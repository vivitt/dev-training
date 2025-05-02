# Count Semiprimes Values

A semiprime is a number that is the product of two (same or different) prime numbers.

In this exercise, given two arrays P and Q with the same length, the goal is to find out how many semiprime numbers are there between P[i] and Q[i].
The function must return an array where each element corresponds to the count of semiprimes within the query range.

```
function solution(N, P, Q) {
    const isPrime = Array(N+1).fill(true)
    isPrime[0] = isPrime[1] = false
    for(let i = 2; i <= N; i++) {
        for(let j = i*i; j <= N; j += i) {
            isPrime[j] = false
        }
    }

    const isSemiprime = Array(N+1).fill(false)

    for(let i = 2; i <= Math.floor(N/2); i++) {
        for(let j = i; j <= Math.floor(N/2); j++) {
            if(isPrime[j] && isPrime[i] && i*j <= N) {
                 isSemiprime[j*i] = true
            }
           
        }
    }


    const countSemiprimes = Array(N+1).fill(0)


    for(let i = 1; i <= N; i++) {
        countSemiprimes[i] = countSemiprimes[i-1]
        if(isSemiprime[i]) {
            countSemiprimes[i]++
        } 
        
    }

    const result = []
    for(let i = 0; i < P.length; i++) {
        const count = countSemiprimes[Q[i]] - countSemiprimes[P[i]-1]

        result.push(count)
        
    }
    return result
}
```
