In this exercise, the goal is to create a function that answers multiple queries.

Each query specifies a particular segment of a given DNA sequence, and the function should return the minimal impact factor of the nucleotides within that segment.

```
// you can write to stdout for debugging purposes, e.g.
// console.log('this is a debug message');

function solution(S, P, Q) {
    // Implement your solution here
    const factors = {
        A: 1,
        C: 2,
        G: 3,
        T: 4
    }

    const replaced = S.split('').map((el=> factors[el]))

    let p = P[0]
    let q = Q[0]
    
    let currentMin = 4

    const results = []

    for(let i = 0; i < P.length; i++) {
        results.push( Math.min(...replaced.slice(P[i], Q[i]+1)))

    }
    
    return results
}

```
