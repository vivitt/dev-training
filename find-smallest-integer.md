# Find the Smallest Missing Positive Integer

The goal of this exercise is to find the smallest positive integer missing from an array.
First, create a new array without duplicates and without negative numbers.
Then, handle edge cases like an array with no positive integers or just one element.
Next, create a third array to track occurrences and iterate over the unique values to count them.
Finally, return the first number with zero occurrences or the maximum value plus one.


```
function solution(A) {
    const uniques = [...new Set(A)].filter((el) => el > 0)

    if(!uniques[0])return 1
    if(!uniques[1]) return uniques[0] === 1 ?2 :1

    const max = Math.max(...uniques)

    const counter = Array.from({length: uniques.length}, el => el = 0)
    
    for(let i = 0; i < uniques.length; i++) {
        counter[uniques[i]-1]++
    }

    return counter.indexOf(0) === -1 ?max+1 :counter.indexOf(0)+1
}
```
