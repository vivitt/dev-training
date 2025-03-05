The goal of this exercise is to find the smallest positive integer not included in an array.

```
// you can write to stdout for debugging purposes, e.g.
// console.log('this is a debug message');

function solution(A) {
    // Implement your solution here
    let uniques = [... new Set(A)]
    let max = Math.max(...uniques)

    let comp = 0 ^ max
    for(let i = 0; i < uniques.length; i++) {
        console.log(comp)
        comp ^= A[i]
    }

    return comp === max ? max +1 : comp
}
```
