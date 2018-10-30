---
title: 'Codility: PermCheck'
categories: Algorithm
date: 2018-05-08 19:03:45
tag: Codility
---
https://app.codility.com/demo/results/trainingFMU4FV-EGR/
```javascript
function solution(A) {
  A.sort((a, b) => a - b);

  for (var i = 0; i < A.length; i++) {
    if (A[i] !== i+1) {
      return 0;
    }
  }
  return 1
}

```


https://app.codility.com/demo/results/trainingAAH8ZP-A7Z/
```javascript
function solution(A) {
  A.sort((a, b) => a - b);
  return Number(A.every((elem, idx) => elem === idx + 1));
}
```

