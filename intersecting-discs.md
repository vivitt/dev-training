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

A more efficient solution is based on calculating the number of currently intersecting circles, assuming that each new circle intersects with the previous ones unless certain conditions are met.
1. Create two arrays:
- One to store the starting points of each circle.
- Another to store the end points.
Then, sort both arrays in increasing order.

2. Initiate three variables:
- pairs to keep track of intersecting pairs.
- end to track the current position in the ends array.
- currentCircles to count how many circles are currently active (meaning they can still intersect with new circles).

3. Count intersecting circles:
Iterate through each circle (using the sorted starts array).
For each circle, check if the smallest end point (ends[end]) is smaller than the current start point (starts[i]).
If true, it means that circle is no longer active, so decrease currentCircles and move the end forward.
If the above condition isn’t met, the new circle intersects with all currently active circles.
Add currentCircles to pairs and increment currentCircles to account for the new circle.
If at any point pairs exceeds 10000000, return -1, otherwise end the loop and return the number of pairs.

```
function solution(A) {
    
    const l = A.length

    const starts = Array(l).fill(0)
    const ends = Array(l).fill(0)

    for (let i = 0; i < l; i++) {
        starts[i] = i - A[i]
        ends[i] = i + A[i]
    }

    starts.sort((a, b) => a - b)
    ends.sort((a, b) => a - b)

    let pairs = 0
    let end = 0
    let currentCircles = 0
    

    for(let i = 0; i < l; i++) {
        while (end < l && ends[end] < starts[i]) {
            currentCircles--
            end++
        }
        pairs += currentCircles
        if(pairs > 10000000) return -1
        currentCircles++
    }
    return pairs
}
```
