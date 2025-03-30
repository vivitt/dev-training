# Find Dominator Index

Write a function that returns any index of the dominator element in an array or -1 if the array has no dominator.
An element is considered a dominator if it occurs in more than half of the elements in the array.
```
function solution(A) {
    const l = A.length
    let current = A[0]
    let count = 1

    for(let i = 1; i < l; i++) {
        if(count === 0) {
            current = A[i]
            count = 1
        } else {
            if(A[i] === current) {
                count+= 1
            } else {
                count-= 1
            }
        }
    }
    
    if(count === 0) return -1
   
    let occurrences = 0
    let index = -1
    for(let i = 0; i < l; i++) {
        if(A[i] === current) {
            occurrences++
        }
    }
    if(occurrences > l/2) {
        index = A.indexOf(current)
    }
    
    return index
}
```
