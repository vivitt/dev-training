# Living Fish Exercise

In this exercise, the goal is to write a function that calculates the living fish.
The function receives two arrays of the same size: Array A stores the size of the fish, and Array B, their directions.
When two fish meet, only the biggest stays alive. So, the goal is to get the number of fish that will survive.

First, check if the array of directions includes both 0 and 1. Otherwise, you can return the array's length.
Then, create two arrays to use as a stack for living fish. One will store directions and the other the values of each fish.
Iterate through the array of fish. If the direction of the fish is 1, push its value and direction to the current alive fish arrays.
Otherwise, iterate through the currently living fish and check whether the last element of the stack can meet the current fish.
When the fish meet a fish in the stack with the same direction, it can be pushed to the alive arrays. Otherwise, keep iterating and only keep the biggest fish in the array.

At the end, return the length of the array of living fish.

```
function solution(A, B) {
    const dirs = [B[0]]
    const values = [A[0]]

    for(let i = 1; i < A.length; i++) {
        if(B[i] === 1) {
            dirs.push(B[i])
            values.push(A[i])
        } else {
            const l = dirs.length
            const last = dirs[l-1]
            if(last === 0) {
                dirs.push(B[i])
                values.push(A[i]) 
            } else {
                
                for(let j = l-1; j >= 0; j--) {
                    if(dirs[j] === 0) {
                        dirs.push(B[i])
                        values.push(A[i]) 
                        j = -1
                    } else if(values[j] > A[i]) {
                        j = -1
                    } else {
                        dirs.pop()
                        values.pop()
                        if( j === 0) {
                            dirs.push(B[i])
                            values.push(A[i]) 
                        }
                    }
                }
            }
        }
    }
    return values.length
}
```
