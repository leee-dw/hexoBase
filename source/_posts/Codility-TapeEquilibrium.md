---
title: 'Codility: TapeEquilibrium'
categories: Algorithm
date: 2018-05-04 16:45:15
tag: Codility
---

```javascript
function solution(A) {
  let res = [];
  let init = A[0]
  let rest = A.slice(1).reduce((a, b) => a + b);
  res.push(Math.abs(init - rest));

  for (var i = 1; i < A.length - 1; i++) {
    init += A[i];
    rest -= A[i];
    res.push(Math.abs(init - rest));
  }
  return Math.min(...res)
}
```

https://app.codility.com/demo/results/training9E5VGN-R9C/