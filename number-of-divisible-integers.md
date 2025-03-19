# Find all divisible integers
In this exercise, the solution function receives three arguments: A, B, and K.
The goal is to find how many integers within the range [A..B] are divisible by K.

First, calculate the largest value within the range that is divisible by K.
Then, divide it by K to get the count of divisible numbers from 1 to B.
Finally, adjust for the values before A by subtracting the count of numbers divisible by K from 1 to A-1.

```
function solution (A, B, K) {
    return ((B - B%K) / K) - Math.floor((A - 1)/ K)
}
```
