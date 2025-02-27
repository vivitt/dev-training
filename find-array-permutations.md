The goal of this task is to create a function to determine whether an array of N integers is a permutation.

A permutation is a sequence that contains each element from 1 to N exactly once.

My solution stores the maximum value in a variable and calculates the expected permutation sum for this value.
Then, it creates a Set to remove all repeated elements. If the array length is greater than the set size, it returns 0, as it contains duplicate numbers.

If the array doesn't have repeated elements, it calculates the current sum of all set elements and compares it with the expected one.
It returns 1 if they are equal and 0 otherwise.

```
function solution(A) {
    // Implement your solution here
    const max = Math.max(...A)

    const targetSum = max * (max + 1) / 2

    const ASet = new Set(A);
    if(ASet.size < A.length) return 0

    const currentSum = [...ASet].reduce((acc, el) => acc + el, 0);

    return targetSum === currentSum ?1 :0

}
```
