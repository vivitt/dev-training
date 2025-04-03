# Find the max profit

Given an array of stock prices for consecutive days, find the best day to buy and sell to maximize profit.

If there's no possible profit, return 0.

```
function solution(A) {
    let profit = 0

    const l = A.length

    let min_value = A[0]
    let max_slice = A[1]

    for(let i = 1; i < l-1; i++){
        min_value = Math.min(min_value, A[i])

        max_slice = Math.max(A[l-1], A[i+1])

        const diff = max_slice - min_value

        if(diff > profit) {profit = diff}
    }
    return profit
}
```
