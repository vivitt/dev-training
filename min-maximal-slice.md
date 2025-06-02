# Minimal Maximal Division

Given an array A, consisting of L elements, each no greater than M, the goal in this exercise is to find the minimal possible maximum sum when dividing the array into K blocks.

```
function solution(K, M, A) {
    const L = A.length
    let max = A.reduce((acc, el) => acc+el)
    let min = M
    let result = max

    const isValidBlock = (mid, k, arr) => {
        let sum = 0;
		for (i = 0; i < arr.length; i++) {
			sum += arr[i];
			if (sum > mid) {
				sum = arr[i];
				k--;
			}
			if (k < 0) {
				return false;
			}
		}
		return true;
    }

    while(min <= max) {
        const mid = Math.floor((min+max) / 2)
        if(isValidBlock(mid, K-1, A )) {
            max = mid - 1;
			result = mid;
		} else {
			min = mid + 1;
		}
    }
    return result;
}
```
