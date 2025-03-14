# Find Minimal Average of Possible Array Slices

The goal in this exercise is to write a function that receives an array of integers and returns the first index of the slice with the minimal average sum. The average sum is calculated by dividing the sum of the elements by the number of elements in the slice.

There’s something important to be aware of before approaching this problem. The best slice will always have two or three elements, as any slice longer can be broken down into smaller slices with a lower or equal average.
So in my solution, I will calculate and compare all possible slices of two or three elements.

First, store the length of the starting array in a variable.
Next, create a new array to store the prefix sums of all the elements in the original array, and two variables to store the last minimal average and the corresponding starting index, initialized to the average of all elements and 0, respectively.
Iterate through the first array, comparing the average value of the two-element and three-element slices starting at the current index. If any of those values is smaller than the last minimal average variable value, update it and also update the index to be returned as the result.


```
function solution(A) {
    const l = A.length
    const prefixSum = Array.from({length: l+1}, el => el = 0)

    for (let i = 1; i<l+1; i++) {
        prefixSum[i] = prefixSum[i-1] + A[i-1]
    }

    let minAvr = prefixSum[l] / l
    let minIndex = 0

    for(let i = 0; i< l; i++) {
        if((prefixSum[i+2] -prefixSum[i]) / 2 < minAvr) {
            minAvr = (prefixSum[i+2] -prefixSum[i]) / 2
            minIndex = i
        }
        if((prefixSum[i+3] -prefixSum[i]) / 3 < minAvr) {
            minAvr = (prefixSum[i+3] -prefixSum[i]) / 3
            minIndex = i
        }
    }

    
    
    return minIndex
}
```
