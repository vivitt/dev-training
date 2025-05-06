# Counting Eaten Chocolates

In this exercise, there's a circle with N chocolates. You start at position 0 and eat chocolates by jumping M spaces each time.
The goal is to find out how many chocolates you can eat before reaching a spot where the chocolate has already been eaten.

To find the solution, I started with the condition `(M * X) % N === 0`, which means `M * X` must be a multiple of N.
That gives us the equation `M * X = k * N` for some integer k, so `X = (k * N) / M`.
For X to be a whole number, `(k * N) / M` must be an integer. To find the smallest such X, we use the greatest common divisor of M and N.
So the smallest possible value for X is `X = N / gcd(M, N)`.

```
function solution(N, M) {

    const gcd = (a, b) => b === 0 ? a : gcd(b, a % b);
    const d = gcd(M, N);

    return N / d
}
```
