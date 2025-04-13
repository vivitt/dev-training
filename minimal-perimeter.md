# Find the minimal perimeter

A rectangle’s area is equal to `A * B`, where `A` and `B` are the lengths of its sides. Its perimeter is calculated as `(A + B) * 2`.

In this task, you are given a number N representing the area of a rectangle.
The goal is to find the minimal possible perimeter of a rectangle that has this area.

```
function solution(N) {
    let A = 1
    let B = N
    let perimeter = (A+B) * 2

    while (A<=B) {
        A++
        B = N/A
        perimeter = Number.isInteger(B) ?(A+B) * 2 :perimeter
    }
    return perimeter
}
```
