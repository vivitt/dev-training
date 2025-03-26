# Nesting Strings

The solution in this exercise is a function that returns 1 if a string is properly nested and 0 if it isn’t.

Strings consist of ( and ) characters, and a properly nested string meets one of the following conditions:

- It is an empty string.

- It has the form (S), where S is a properly nested string.

- It has the form SS, where both S are properly nested strings.

My solution iterates through the string and uses an array to store the opening characters.
It adds an open parenthesis to the stack each time the loop finds one.
If the loop finds a closing parenthesis, it pops one opening parenthesis from the stack and continues only if the popped element is an opening parenthesis.
If not, it returns 0.
At the end of the loop, it returns 0 if there are still elements without a closing match in the stack. Otherwise, it returns 1.

```
function solution(S) {
    const stack = []
    if(S.length === 0) return 1
    for(let i = 0; i < S.length; i++) {
        if (S[i] === '(') {
            stack.push('(')
        } else {
            const open = stack.pop()
            if (open !== '(') return 0
        }
    }
    return stack.length > 0 ?0 :1
}
```
