# Nested Strings

The solution should return 1 when the received string is properly nested and 0 otherwise. A string is properly nested when:

- It is empty

- It is a properly nested string wrapped by '()', '[]', or '{}'

- It is a concatenation of two properly nested strings


The solution consists of creating an object to store the matching characters and an array to store the stack currently being evaluated.
Iterate through the characters in the string. If the character is within the pairs object's values, add it to the stack.
If it is not a value in the pairs object, that means it is a closing element. So, if the stack is empty, return 0 as it has no matching opening character.
Otherwise, check if it matches the last element in the stack array and return 0 if it doesn't.
At the end, if the stack is empty, return 1. Otherwise, return 0.

```
function solution(S) {
    const pairs = {
        '}' : '{',
        ']' : '[',
        ')' : '('
    }

    let stack = []

    for (let i = 0; i < S.length; i++) {
        if(Object.values(pairs).includes(S[i])) {
            stack.push(S[i])
        } else if (pairs[S[i]]) {
            if (!stack[0] || stack.pop() !== pairs[S[i]]) {
                return 0
            }
        }
    }
    if(stack.length === 0) return 1

    return 0
}
```
