# Count the number of equi leaders

In this exercise, the task is to find how many slices within an array have the same leader element or equi leader.
A leader is an element that occurs at least more than half the array length.

```
function solution(A) {
    // Implement your solution here
    let equiLeaders = 0
    let count = 1
    let current = A[0]
    for(let i = 1; i < A.length; i++) {
        if(count === 0) {
            current = A[i]
            count = 1
        }  else {
            if( A[i] === current){
                count++
            } else {
                count--
            }
        }
    }
            
    if(count === 0) {
        return equiLeaders
    } else {
        let occurrences = 0
        for(let i = 0; i < A.length; i++) {
            if(A[i] === current) {
                occurrences++
            }
        }
        if(occurrences <= A.length/2) {
            return equiLeaders
        } else {
            let candidate = current

            for(let i = 0; i < A.length; i++) {
                if(i % 2 === 0) {
                    const left = A.slice(0, i+1)
                    const rigth = A.slice(i+1)

                    let counter = 0
                    for(let j = 0; j < left.length; j++) {
                        if(left[j] === candidate) {
                            counter++
                        }
                    }
                    if(counter > left.length/2) {
                    counter = 0
                    for(let j = 0; j < rigth.length; j++) {
                        if(rigth[j] === candidate) {
                                counter++
                        }
                    }
                    
                    if(counter > rigth.length/2) {
                        equiLeaders++
                    }
                }
                }
            
            }
        
        }

    }
    return equiLeaders
}
```
