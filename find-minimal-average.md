The goal of this exercise is to write a function that receives an array of integers and returns the first index of the slice with the minimal average sum.
The average sum is calculated as the sum of the elements divided by the number of elements in a possible slice.

First, store the given array's length in a variable.

Create a new array to store the prefix sums for all the elements in the first array.

Then iterate trought the array elements and calculate the min average for each posible slice.



```
function solution(A) {
    const l = A.length
    const sum = Array.from({length: l + 1 }, el => el = 0)

    for(let i = 1; i < l +1 ; i++) {
        sum[i] = sum[i - 1] + A[i - 1]
    }
   
    let lastMin = sum[sum.length-1]/l
    let lastIndex = 0
    for(let i = 1; i < l-1; i++) {
        let j = l
        while(j > i) {
            if(sum[j]-sum[i]/(j-1) < lastMin) {
                lastMin = sum[j]-sum[i]/(j-1)
                lastIndex = i
            }
            j--
        }
    }

    return lastIndex
}
```
