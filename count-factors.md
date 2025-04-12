# Count Factors
The goal of this exercise is to count the number of factors of a given number N.
A factor of N is an integer that, when multiplied by another integer, equals N.

In the solution, I count all the divisors of N, which gives me the total number of factors.
If a number i satisfies the condition `i * i < N` and `N % i === 0`, then both `i` and `N / i` are factors, so I add two to the count.
If `i * i === N`, it means i is a square root of N, so I add one final factor.

In the end, I return the total count of factors.

```
function solution(N) {
    let i = 1
    let factors = 0

    while(i*i < N) {
        if(N % i === 0) {
            factors+=2
        }
        i++
    }

    if(i*i === N) {
        factors++
    }

    return factors
}
```
