The goal of this exercise is to write a function that receives an array of integers and returns the first index of the slice with the minimal average sum.
The average sum is calculated as the sum of the elements divided by the number of elements in a possible slice.


```
function solution(A) {
    const l = A.length
    const sum = Array.from({length: l + 1 }, el => el = 0)

    for(let i = 1; i < l +1 ; i++) {
        sum[i] = sum[i - 1] + A[i - 1]
    }

   const posibleSlices = l * (l - 1) / 2
   
   let lastMin = sum[sum.length-1]/l
   let lastIndex = 0

    for(let i = 0; i < posibleSlices+1; i++) {
        let j = sum.length - 1
        while(j > i) {
            if((sum[j] - sum[i])/(l-i) < lastMin) {
                lastMin = (sum[j] - sum[i])/(l-i)
                lastIndex = i
            }
            j--
        }
    }

    return lastIndex
}
```
