# Find the max profit

Given an array of stock prices for consecutive days, find the best day to buy and sell to maximize profit.

If there's no possible profit, return 0.

```
function solution(A) {
    const l = A.length
    let profit = 0

    let last_sell = A[l-1]
    let last_buy = A[0]

    if(last_sell - last_buy > profit) {
        profit = last_sell - last_buy
    }
   

    for(let i = 1; i < l ; i++) {
        
        last_buy = Math.min(last_buy, A[i])
        last_sell = A[i+1]

        const diff = last_sell - last_buy
        if (diff > profit) {profit = diff}
    }

    return profit
}
```
