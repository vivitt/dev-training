In this exercise, the goal is to create a function that answers multiple queries.

Each query specifies a particular segment of a given DNA sequence, and the function should return the minimal impact factor of the nucleotides within that segment.

This solution works but has a O(N * M) time complexity, so it doesnt pass test when the number of queries is big.
```


function solution(S, P, Q) {
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

🚧 WIP To achieve a time complexity of O(n+m) 
```
function solution(S, P, Q) {

   
    
    const factors = {
        A: 1,
        C: 2,
        G: 3,
        T: 4
    }

    const replaced = S.split('').map((el=> factors[el]))
const sum = Array.from({length: replaced.length + 1 }, el => el = 0)

 const q = P.length
    const results = []

    for(let i = 1; i < replaced.length+1; i++) {
        sum[i] = sum[i - 1] + replaced[i - 1]
    }

    

    for(let i = 0; i < q; i++) {
        const elements = Q[i] - P[i] + 1
        const diff = sum[Q[i]] - sum[P[i]]
        if(diff === 0) {
            results.push(replaced[Q[i]])
        } else {

            let index = P[i]
            let min = replaced[P[i]]
            while(min > 1 && index <= Q[i]) {
                if(replaced[index+1] < min) {
                    min = replaced[index+1]   
                }
                index++
            }
            results.push(min)

        }
    }
    

    return results
}
```
