# Find the number of intersecting discs

In this exercise, the goal is to write a function that receives an array of positive integers and calculates intersecting discs, assuming:
- discs are drawn in a plane
- disc radius is equal to A[index]
- the disc center is placed at index.
  
If there are more than 10,000,000 pairs of intersecting discs, the function should return -1.
Otherwise, it should return the number of pairs of intersecting discs.

```
function solution(A) {
  let pairs = 0
  for (let i = 1; i < A.length; i++) {
    for (let j = 0; j < i; j++) {
      if(i - A[i] <= j + A[j]) {
        pairs++  
      }
      if (pairs > 10000000) return -1
    }
  }
  return pairs
}
```
