The goal of this exercise is to write a function that receives an array of integers and returns the first index of the slice with the minimal average sum. The average sum is calculated by dividing the sum of the elements by the number of elements in the slice.

First, store the length of the given array in a variable.

Next, create a new array to store the prefix sums of all the elements in the original array.

Then, create two variables: one to store the current minimum average of a slice, and another to store the index of the starting slice. Initialize these variables with the average of the sum of all elements and the index 0.

Now, iterate through the array and calculate the minimum average for each possible slice. If the average is smaller than the last minimum average, update the value and the index. Return the last stored index value.

```
function solution(A) {
    const l = A.length
    const prefixSum = Array.from({length: l+1}, el => el = 0)

    for (let i = 1; i<l+1; i++) {
        prefixSum[i] = prefixSum[i-1] + A[i-1]
    }

    let minAvr = prefixSum[l] / l
    let minIndex = 0

    for(let i = 0; i < l; i++) {
        let endSlice = l
        let elements = l - i
        while(endSlice > i && elements > 1) {
            const avr = (prefixSum[endSlice] - prefixSum[i]) / elements
            
            if (avr < minAvr) {
            minAvr = avr
            minIndex = i   
        }
        endSlice--
        elements--
        }   
    }
    return minIndex
}
```

The previous solution is okay, but it has a time complexity of O(N²) and fails the test cases for large numbers. An attempt at a more performant solution is the following, but it only works when the optimal slice has a length of two elements.

```
function solution(A) {
    const l = A.length
    const prefixSum = Array.from({length: l+1}, el => el = 0)

    for (let i = 1; i<l+1; i++) {
        prefixSum[i] = prefixSum[i-1] + A[i-1]
    }

    let minAvr = prefixSum[l] / l
    let minIndex = 0

    for(let i = 2; i < l+1; i++) {
       if(prefixSum[i]/i < minAvr) {
           minAvr = prefixSum[i]/i
           minIndex = i-2
       }
    }
    for(let i = 0; i< l; i++) {
        if((prefixSum[i+2] -prefixSum[i]) / 2 < minAvr) {
            minAvr = (prefixSum[i+2] -prefixSum[i]) / 2
           minIndex = i
        }
    }
    
    return minIndex
}
```
