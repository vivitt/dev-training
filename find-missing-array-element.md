# Find the missing array element

The goal of this exercise is to find the missing element in an array.

The array contains all unsorted integers within a range except for one, which the solution should return.
This problem can be solved in O(n) time complexity.
First, check if the array is empty. Then get the max element in the range.
If the max element is equal to the array length, it means that there is no missing element so it returns max + 1.
Otherwise, compare and return the difference between the expected sum for the range from 1 to max and the current array sum.


```
function solution(A) {
    // Implement your solution here
    
    if(A.length === 0) return 1

    const max = Math.max(...A)

    if(max === A.length) return max+1

    const expected_sum = max * (max + 1) / 2

    const current_sum = A.reduce((acc, el) => acc+el)

    return expected_sum - current_sum
}
```


