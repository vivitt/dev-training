# Count Semiprimes Values

A semiprime is a number that is the product of two (same or different) prime numbers.

In this exercise, given two arrays P and Q of the same length, the goal is to find how many semiprime numbers exist between P[i] and Q[i] for each query.
The function must return an array where each element corresponds to the count of semiprimes within the respective query range.

The solution uses the *Sieve of Eratosthenes* to first identify all prime numbers up to a given number N.
This technique involves creating an array of size `N + 1`, used to track prime numbers.
Start with `i = 2` as it is the first prime number, and iterate through the array up to N, marking all multiples of `i` as non-prime.
Then, increment `i` and repeat the process until `i` exceeds the square root of N.

Once all prime numbers up to N are identified, compute all semiprime numbers by multiplying pairs of primes.

Next, build a prefix sum array to count how many semiprimes appear up to each index.

Finally, return a result array, where each element contains the number of semiprimes corresponding to each query range.

```
function solution(N, P, Q) {
    const isPrime = Array(N+1).fill(true)

    isPrime[0] = isPrime[1] = false

    for(let i = 2; i <=N;i++) {
        for(let j = i*i; j <= N; j += i) {
            isPrime[j] = false
        }
    }

    const isSemiprime = Array(N+1).fill(false)


     for(let i = 2; i <= Math.floor(N/i);i++) {
        for(let j = i; j <= Math.floor(N/i); j ++) {
            if(isPrime[i] && isPrime[j] ) {
                if(i*j > N) break;
                isSemiprime[i*j] = true
            }
        }
    }

    const countSemiprimes = Array(N+1).fill(0)
    for(let i = 4; i <=N;i++) {
        countSemiprimes[i] += countSemiprimes[i-1]
        if(isSemiprime[i])countSemiprimes[i]++
    }

    const result = []
    for(let i = 0; i < P.length; i++) {
        result.push(countSemiprimes[Q[i]] - countSemiprimes[P[i]-1])
    }
    return result

}
```
