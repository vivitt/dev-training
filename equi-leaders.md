# Count the number of equi leaders

In this exercise, the task is to find how many slices within an array have the same leader element or equi leader.
A leader is an element that occurs at least more than half the array length.

```
function solution(A) {
    let pairs = 0
    let last = 0
    let count = 0

    for(let i = 0; i < A.length; i++) {
        if(count === 0) {
            last = A[i]
            count++
        } else {
            if(A[i] !== last) {
                count--
            } else {
                count++
            }
        }
    }

    if(count === 0) {return pairs}
    
    const candidate = last
    let occurrences = 0

    const prefix = Array.from({length: A.length+1}).fill(0)
    for(let i = 0; i < A.length; i++) {
        if(A[i] === candidate) {
            occurrences++ 
        }
        prefix[i+1] = occurrences
    }

    if(occurrences <= A.length/2) {return pairs}

    for(let i = 0; i < A.length; i++) {
        
            const left = prefix[i + 1] - prefix[0]
            const rigth = prefix[prefix.length-1] - prefix[i+1]
            const left_l = i+1
            const rigth_l = A.length - left_l
            if(left > left_l/2 && rigth > rigth_l/2) {
                pairs++
            }
          
    }
    return pairs
}
```
