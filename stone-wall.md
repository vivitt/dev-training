# Build a Stone Wall

In this exercise, the task is to create a wall of length N with a height of H[i] at each point.
The solution should return the lowest number of stones needed.
```
function solution(H) {
    let blocks = 1
    let currentBlocks = [H[0]]
    for(let i = 1; i < H.length; i++) {
        let currentH = currentBlocks.reduce((acc, el) => {
            return acc + el
        })
        if(H[i] > currentH) {
            currentBlocks.push(H[i] - currentH)
            blocks++    
        } else if (H[i] < currentH) {
            const l = currentBlocks.length
            for(let j = l-1; j >= 0; j--) {
                const last = currentBlocks.pop()
                currentH -= last
                if(currentH < H[i]) {
                    currentBlocks.push(H[i] - (currentH ))
                    blocks++
                    j=-1
                } else if (currentH ===H[i]) {
                    j=-1
                } 
            }
        }
    }
    return blocks
}
```
