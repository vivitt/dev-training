# Fibonacci Frog

A small frog wants to cross the river. Starting from position -1, the frog must reach the other side at position N.
The frog can only jump onto leaves, represented by an array A, where each 0 is water and each 1 is a leaf.

The frog can jump any distance F(K), where F(K) is the K-th Fibonacci number.
The Fibonacci sequence is defined as:
```
F(0) = 0
F(1) = 1
F(M) = F(M-1) + F(M-2), if M >= 2
```

The solution must return the minimum number of jumps the frog must take to reach the other side, or -1 if it is not possible to cross.

```
function solution(A) {
    const goal = A.length
    if(goal <= 2) return 1
    const fib = [0, 1]

    for(let i = 1; i < goal && fib[i] <= goal; i++) {
        fib[i+1] = fib[i] + fib[i-1]
    }

    const stack = [[-1, 0]]
    let minJumps = -1

    while(stack[0]) {
        let [position, jumps] = stack.pop()
        if(minJumps === -1 || jumps < minJumps-1) {
            for(let i = 2; i < fib.length && fib[i] <= goal-position; i++) {
            if(position+fib[i] === goal) {
                minJumps = jumps+1 
            }
            if(A[position+fib[i]] === 1) {
                stack.push([position+fib[i], jumps+1])
            }
        }
        }
        
    }
    return minJumps
}
```
