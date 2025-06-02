# Minimal Maximal Division

Given an array A, consisting of L elements, each no greater than M, the goal in this exercise is to find the minimal possible maximum sum when dividing the array into K blocks.

```
function solution(K, M, A) {
    let max = A.reduce((acc, el) => acc + el, 0)
    let min = Math.max(...A)

    let result = max

    while(min <= max) {
        const mid = Math.floor((max + min) / 2)

        let blocks = 1
        let sum = 0

        for(let num of A) {
            if(sum + num <= mid) {
                sum += num
            } else {
                sum = num
                blocks++
            }
        }

        if(blocks <= K) {
            result = mid
            max = mid - 1

        } else {
            min = mid + 1
        }
    }
    return result
}
```

This solution uses the Binary Search Algorithm, which lets us check whether the result should be smaller or larger than a given number.
With each iteration, the possible range gets halved, so the time complexity is O(N*log(N+M)).
