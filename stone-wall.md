# Build a Stone Wall

In this exercise, the task is to create a wall of length N with a height of H[i] at each point.
The solution should return the lowest number of stones needed.
```
function solution(H) {
    const wall = [H[0]]
    let lastHeigth = H[0]
    let blocks = 1
    for(let i = 1; i < H.length; i++) {
        if(H[i] > lastHeigth) {
            wall.push( H[i]-lastHeigth)
            lastHeigth = H[i]
            blocks++
        } else if (H[i] < lastHeigth) {
            const l = wall.length
            for(let j = l-1; j >= 0; j--) {
                const lastBlock = wall.pop()
                lastHeigth -= lastBlock
                if(lastHeigth  < H[i]) {
                    wall.push(H[i] - (lastHeigth))
                    lastHeigth = H[i]
                    blocks++
                    j = -1
                } else if (lastHeigth  === H[i]) {
                    j = -1
                }
            }
        }
    }
    return blocks
}
```
