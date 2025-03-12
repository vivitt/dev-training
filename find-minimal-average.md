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
        while(endSlice > i) {
            const avr = (prefixSum[endSlice] - prefixSum[i]) / element
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
