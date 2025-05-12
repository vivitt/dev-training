# Common Prime Divisors

In this exercise, the goal is to count how many pairs of integers have exactly the same number of prime divisors.
A prime number X is called a prime divisor of a positive integer Y if it can be multiplied by some other positive integer Z such that `X * Z = Y`.

The solution function receives two arrays, A and B, of the same length, and must return the number of pairs where A[i] and B[i] have exactly the same number of prime divisors.

```
function solution(A, B) {
    const l = A.length
    const gcd = (a, b) => a%b === 0 ?b :gcd(b, a%b)
    const reduce = (val, common) => {
        const g = gcd(val, common)
        if(val === 1) return val
        if(g === 1) return val
        return reduce(val/g, common)
    }
    let count = 0
    for(let i = 0; i < l; i++) {
        let [max, min] = [Math.max(A[i], B[i]), Math.min(A[i], B[i])]
        while (max > 1 && gcd(max, min) > 1) {
            max = reduce(max, gcd(max, min) )
        }
        if(max === 1)count++
    }
    return count
}
```
