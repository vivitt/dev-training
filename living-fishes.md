# Living Fish Exercise

In this exercise, the goal is to write a function that calculates the living fish.
The function receives two arrays of the same size: Array A stores the size of the fish, and Array B, their directions.
When two fish meet, only the biggest stays alive. So, the goal is to get the number of fish that will survive.

First, create an array to store the fish going to the right, with a direction equal to 1.
Initialize a variable to count living fish.

Iterate through the array of directions. If the direction is 0 and the stack is empty, add 1 to the counter. Otherwise, if the direction is 1, add it to the stack. If it is 0 but the stack already has elements in it, the fish meet.
Then, if the last fish is bigger than the previous one, add 1 to the counter and continue comparing fish until the stack is empty. If the previous one is bigger, keep the stack and continue the loop.

Finally, return the counter plus the fish in the stack.

```
function solution(A, B) {
    const stack = []
    let alive = 0
    for(let i = 0; i < A.length; i++) {
        if(B[i] === 1){
            stack.push(A[i])
        } else {
            let last = stack.pop()
            if(last === undefined) {
                alive++
            } else {
                if (last > A[i]) {
                    stack.push(last)
                } else {
                    while(last !== undefined) {
                        alive++
                        last = stack.pop()
                    }
                }
            }
        }
    }
    return alive + stack.length
}
```
