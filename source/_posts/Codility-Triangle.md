---
title: 'Codility: Triangle'
categories: Algorithm
date: 2018-04-15 19:11:08
tag: Codility
---


```javascript
function solution(A) {
  A.sort((a, b) => a - b);
  let count = 0;
  for (let i = 0; i < A.length - 1; i++) {
    if (A[i] + A[i + 1] > A[i + 2]) {
      count++;
    }
  }
  return count === 0 ? 0 : 1;
}
```

for문을 사용하지 않고 문제를 풀 수 있는 방법을 생각하자.

https://app.codility.com/demo/results/trainingVFKUAM-HY8/
