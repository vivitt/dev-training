# Array of Counters

In this exercise, you start with N counters, all set to 0.
You can perform two operations on these counters:
  - add 1 to a specific counter
  - set all counters to the highest counter value
    
You also get an array A of integers, where each element represents an operation:
  - if A[K] ≤ N, increase the counter at index A[K] - 1 by 1
  - if A[K] > N, set all counters to the current maximum counter value

First, create an array of N elements, all initialized to 0 (this will be the counters array).
Then, create a variable to track the max counter value and another one to store the last max value applied to all counters (when A includes a value greater than N). Initialize both variables to 0.

Now, loop through A. If A[i] is greater than N, update maxCounterApplied with the current max counter value.
Otherwise, check if the counter at A[i] is smaller than maxCounterApplied. If so, update it to match maxCounterApplied + 1. If the counter at A[i] is equal or bigger than maxCounterApplied, then increase the counter at A[i] by 1.
Any time a counter is updated, check if its value is bigger than the maxCounter value to keep it updated. 
Once the loop is done, update any remaining counters that haven't been set properly with maxCounterApplied, and return the counters array.

```
function solution(N, A) {
    const counters = Array.from({length: N}, el => el = 0)
    let maxCounter = 0
    let maxCounterApplied = 0

    for(let i = 0; i < A.length; i++) {
        if(A[i] > N) {
            maxCounterApplied = maxCounter
        } else {
            if(counters[A[i]-1] < maxCounterApplied) {
             counters[A[i]-1] = maxCounterApplied+1   
            } else {
                counters[A[i]-1]++
            }
            maxCounter = Math.max(maxCounter, counters[A[i]-1])
        }         
    }
    return counters.map((el) => {
        return el < maxCounterApplied ?maxCounterApplied :el
    })
}


```

