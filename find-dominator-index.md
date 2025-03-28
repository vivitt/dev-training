# Find Dominator Index

Write a function that returns any index of the dominator element in an array or -1 if the array has no dominator.
An element is considered a dominator if it occurs in more than half of the elements in the array.
```
function solution(A) {
    const l = A.length
    let candidate = A[Math.ceil(l/2)]
    let count = 0
    for(let i = 0; i < A.length; i++) {
        if(A[i] === candidate) {
            count++
        }
    }
    return count > l/2 ?Math.ceil(l/2) :-1
}
```
