The goal of this exercise is to find the minimal possible difference between two parts of a split non-empty array.

The solution function receives an array A of integers and should return an integer representing the minimal difference achieved.

First, create two variables to store the values of the left and right parts of the array. The left part is initialized with the value of the element at index 0, and the right part with the sum of all elements minus the one at index 0.

The difference between these two values is stored in another variable.

Now, it is possible to iterate over all elements of the array, starting from the one at index 1. For each iteration, add the value of A[i] to the left variable and subtract it from the right variable.

Then, check if the difference is less than the last stored value. If at any point the difference equals 1, return this value, as it is the minimum possible. Otherwise, end the loop and return the value of diff.

```
function solution(A) {
    let left = A[0]
    let rigth = A.reduce((acc, el ) => acc+el) - left
    let diff = Math.abs(left-rigth)
    for(let i = 1; i<A.length-1; i++) {
        if(diff === 1) return diff
        left+=A[i]
        rigth-=A[i]
        if(Math.abs(left-rigth) < diff) diff = Math.abs(left-rigth)
    }
    return diff
    
}
```

