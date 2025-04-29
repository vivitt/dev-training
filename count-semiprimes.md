# Count Semiprimes Values

A semiprime is a number that is the product of two (same or different) prime numbers.

In this exercise, given two arrays P and Q with the same length, the goal is to find out how many semiprime numbers are there between P[i] and Q[i].
The function must return an array where each element corresponds to the count of semiprimes within the query range.

```
function solution(N, P, Q) {
    const isPrime = Array(N + 1).fill(true);
    isPrime[0] = isPrime[1] = false;

    for (let i = 2; i * i <= N; i++) {
        if (isPrime[i]) {
            for (let j = i * i; j <= N; j += i) {
                isPrime[j] = false;
            }
        }
    }

    const primes = []
    for (let i = 2; i <= N; i++) {
        if (isPrime[i]) primes.push(i);
    }

    const isSemiprime = Array(N + 1).fill(0);

    for (let i = 0; i <= primes.length; i++) {
        let j = 0
        while(primes[i] * primes[j] <= N) {
            isSemiprime[primes[i] * primes[j]] = primes[i] * primes[j]
            j++
        }
    }

    const result = []

    for(let i = 0; i < P.length; i++) {
        let count = 0
        for(let j = P[i]; j <= Q[i]; j++) {
            if(isSemiprime[j] !== 0) {
                count++
            }

        }
        result.push(count)
    }
    return result
}
```
