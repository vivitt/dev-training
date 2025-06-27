# Find the Maximal Result
In this exercise, you start with an array of integers representing squares on a board.
There is a pebble on square number 0, marking this square.
The goal is to find the maximal possible sum of marked squares, taking into account that the pebble can move at most to the 6 consecutive elements.

The solution uses **dynamic programming**, a method that consists in finding a solution by solving successively similar but smaller problems.
In this case, iterating over the board, calculating the maximal possible sum for each square.

```
function solution(A) {
    const l = A.length

    const movs = Array.from({length: l}).fill(Number.MIN_SAFE_INTEGER)
    movs[0] = A[0]
    for(let i = 1; i < l; i++){
        for(let j = i-1; j >= 0 && j >= i-6; j--) {
            movs[i] = Math.max(movs[i], movs[j] + A[i])
        }
    }
    return movs[l-1]
}
```
