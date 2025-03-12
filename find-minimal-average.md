The goal of this exercise is to write a function that receives an array of integers and returns the first index of the slice with the minimal average sum.
The average sum is calculated as the sum of the elements divided by the number of elements in a possible slice.

First, store the given array's length in a variable.

Create a new array to store the prefix sums for all the elements in the first array.

Then iterate trought the array elements and calculate the min average for each posible slice.



```
function solution(A) {
    const l = A.length
    const prefixSum = Array.from({length: l+1}, el => el = 0)

    for (let i = 1; i<l+1; i++) {
        prefixSum[i] = prefixSum[i-1] + A[i-1]
    }

    let minAvr = prefixSum[l] / l
    let minIndex = 0

    for(let i = 0; i < prefixSum.length; i++) {
        const avr = (prefixSum[i+1] - prefixSum[i]) / (l-i)
        if (avr < minAvr) {
            minAvr = avr
            minIndex = i
            
        }
    }
    return minIndex
}


```
