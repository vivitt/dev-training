# Ladder

Given a ladder with N rungs, you can move up by climbing 1 or 2 rungs at a time.
The goal in this exercise is to find the number of different ways to reach the top of the ladder.

There is an input array A of L elements, each one representing a ladder length, and a second array B of the same length.
The solution function must return an array of the same length, where each number is the number of ways to climb a ladder with A[i] rungs, modulo 2<sup>B[i]</sup>.

```
function solution(A, B) {
    const len = A.length

    const fib = [0, 1]

    for(let i = 2; i <= len+2; i++) {
        fib[i] = BigInt(fib[i-1]) + BigInt(fib[i-2])
    }

    const results = [] 
    for(let i = 0; i < len; i++) {
        results.push(Number(fib[A[i]+1] % BigInt(Math.pow(2, B[i]))))
    }
    return results
}
```
