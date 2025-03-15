# Find the Maximum Triplet Product

The goal of this exercise is to find the maximal product of any triplet in a non-empty array of integers.

```
function solution(A) {
    A.sort((a,b) => b-a)
    return A[0] * A[1] * A[2]
}
```

```
function solution(A) {

    const min = Math.min(...A)
    const max = Math.max(...A)
    const counter = Array.from({length: max - min +1}, el => el = 0)

    for(let i = 0; i < A.length; i++) {
        counter[Math.abs(A[i]-min)]++
    }

    const results = []
    for(let i = counter.length-1; i >= 0; i--) {
        if(results.length === 3) return results[0] * results[1] * results[2]
        
        if(counter[i] === 1) {
            results.push(i+min)
        }
        if(counter[i] > 1) {
           let  added = 0
            while (results.length < 3 && added <= counter[i]){
                results.push(i+min)

            }
           
        }

    }   
}
```
