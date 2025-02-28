In this exercise, you receive N counters, all initialized to 0.
You can perform two operations on these counters:
  - Add 1 to a specific counter
  - Set all counters to the value of the highest counter

You also receive an array A of integers, where each element represents an operation:
  - If A[K] ≤ N, increase the counter at index A[K] - 1 by 1
  - If A[K] > N, set all counters to the maximum counter value

The first step is to create an array of N elements, all initialized to 0. This will be the counters array.
For each value in A, we either add 1 to the element at index A[K] - 1 in the counters array, or if A[K] > N, set all elements in the counters array to its highest value.
To do this, we need to find the maximum value in the counters array and replace all elements with it.
This solution is simple and works for small test cases but fails for larger datasets.

```
function solution(N, A) {
    const counters = Array.from({length: N}).fill(0)

    for(let i in A) {
        if(A[i] > N) {
            const max = Math.max(...counters)
            counters.fill(max)
        } else {
           counters[A[i]-1]++ 
        }
    }
    return counters
}

```

