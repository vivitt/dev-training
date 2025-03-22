# Counting Sort

- In this sorting algorithm, the idea is to first create a counter array and then iterate through it in increasing order. 
- It is necessary to know the range of the sorted values.
- The time complexity is O(n + k)
- Additional memory of O(k) is needed for the counter values.


```
const countingSort = (A, k) => {
  const L = A.length;

  const count = Array(k + 1).fill(0);

  for (let i = 0; i < L; i++) {
    count[A[i]]++;
  }

  let p = 0;
  for (let i = 0; i < count.length; i++) {
    for (let j = 0; j < count[i]; j++) {
      A[p] = i;
      p++;
    }
  }

  return A;
};
```
