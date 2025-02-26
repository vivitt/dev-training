The goal of this problem is to find the array index that represents the first time all integers from 1 to X have appeared in the array.
The solution receives an integer X and an array A as arguments.

My solution creates an array with X elements, and each element is initialized to 0. It also creates a variable to store the current sum of elements.

Then iterates over the A array, and each time it finds a new value, it sets the corresponding index in the count array to 1. It also updates the value of sum by adding 1.

When sum is equal to X, we can return the current value of i. Otherwise, return -1.

```
function solution(X, A) {
    const count = Array.from({length: X}, el => el = 0)
    let sum = 0
    for(let i = 0; i < A.length; i++) {
        if(count[A[i]-1]=== 0){
            count[A[i]-1]++
            sum++
            }
        if(sum === X) return i
        
    }
    return -1
}
```


Other posible solution for this problem uses bitwise operations.
It consists of creating a bitmask to keep track of numbers from 1 to X that have appeared in the array.
The bitmask will be an integer where each bit corresponds to a number in the range 1 to X.

The bitmask is created using the `<<` operator, named the Zero Fill or Bitwise Left Shift operator. It shifts the current bits to the left, pushing zeros in from the right.

For example, if `X = 5`, create the bitmask first by doing `1 << 5`. This operation will shift 5 zeros to the right of the current value, in this case, 1.
The result is `00000000000000000000000000100000`. If we subtract one, it becomes `00000000000000000000000000011111`, which equals 31. We have one 1 bit for each number we need to find in the array.

After having the target, create a current variable to store the value being checked.
Iterate through the array and compare each number by creating a new bitmask for each one, and use the `|` Bitwise OR operator to set bits to 1 if either the current bitmask or the number’s corresponding bit is 1.

When the current bitmask is equal to the target, we can return the index being considered. If that doesn't happen, return -1.

```
function solution(X, A) {
    let target = (1 << X) - 1
    let current = 0  
    for(let i = 0; i < A.length; i++){
        if(A[i] <= X)current |= (1 << (A[i] - 1)) 
        if (current === target)return i
    }
    return -1

}
```



