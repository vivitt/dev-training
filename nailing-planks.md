# Nailing Planks

In this exercise, the input consists of two non-empty arrays of N integers, A and B, representing the starting and ending positions of planks.
There is also a third array of integers C representing positions of nails. A plank is considered nailed if there exists an element C[i] such that `A[k] ≤ C[i] ≤ B[k]`.
The goal is to find the minimum number of nails, that used in order are enough to nail all the planks represented by A and B.
If it is not possible to nail all the planks, the function must return -1.

```
function solution(A, B, C) {
    let min = 1
    let max = C.length
    let nails = -1
    while(min <= max) {
        const mid = Math.floor((min + max) / 2)
        const nailed = new Set()

        for(let i = 0; i < A.length; i++) {
            for(let j = 0 ; j < mid; j++) {
                if(A[i] <= C[j] && C[j] <= B[i]) {
                    nailed.add(i)
                    break;
                }
            }
        }

        if(nailed.size === A.length) {
            nails = mid
            max = mid - 1
        } else {
            min = mid + 1
        }
    }
    return nails
}
```

An optimized solution uses binary search to find the first valid nail, and then to determine the minimum valid index.
This solution has a time complexity of O((N + M) * log M), where N is the number of planks and M is the number of nails:

```
function solution(A, B, C) {
    const sortedNails = C.map((el, ind) => {
        return {value : el, index: ind}
    }).sort((a, b) => a.value - b.value)

    const validNailFound = (start, end, limit) => {
        let left = 0
        let right = sortedNails.length - 1

        let minIndex = Number.MAX_SAFE_INTEGER

        while(left <= right) {
            const mid = Math.floor((left + right) / 2)

            if(sortedNails[mid].value < start) {
                left = mid + 1
            } else {
                right = mid - 1
            }
        }

        for(let i = left; i < sortedNails.length && sortedNails[i].value <= end; i++) {
            if(sortedNails[i].index < minIndex) {
                minIndex = sortedNails[i].index
                if(minIndex <= limit) return true
            }
        }
        return minIndex <= limit
    }

    let min = 0
    let max = C.length

    let nails = -1

    while(min <= max) {
        const mid = Math.floor((min + max) / 2)
        const midIndex = mid - 1
        let allNailed = true

        for(let i = 0; i < A.length; i++) {
            if(!validNailFound(A[i], B[i], midIndex)) {
                allNailed = false
                break
            }
        }

        if(allNailed) {
            nails = mid
            max = mid - 1
        } else {
            min = mid + 1
        }
    }
    return nails
}
```

