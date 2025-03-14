# Find the number of distinct values

The goal in this exercise is to write a function that, given an array of values, returns the number of different elements in it.

It can be solved by creating a Set from the array and returning its size.

```
function solution(A) {
    const set = new Set(A)
    return set.size
}
```
