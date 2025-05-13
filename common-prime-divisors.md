# Common Prime Divisors

In this exercise, the goal is to count how many pairs of integers have exactly the same number of prime divisors.
A prime number X is called a prime divisor of a positive integer Y if it can be multiplied by some other positive integer Z such that `X * Z = Y`.

The solution function receives two arrays, A and B, of the same length, and must return the number of pairs where A[i] and B[i] have exactly the same number of prime divisors.

```
function solution(A, B) {
    const l = A.length
    const gcd = (a, b) => a%b === 0 ?b :gcd(b, a%b)
    const reduceByCommonPrimes = (val, cd) => {
        const g = gcd(val, cd)
        if(g === 1) return val
        val = val/g
        if(val === 1) return val
        return reduceByCommonPrimes(val, g)
    } 

    let count = 0
    for(let i = 0; i < l; i++) {
        const [a, b] = [A[i], B[i]]
        const gr = gcd(a, b)
        const aVal = reduceByCommonPrimes(a, gr)
        const bVal = reduceByCommonPrimes(b, gr)
        if(aVal === 1 && bVal === 1)count++
    }
    return count
}
```
