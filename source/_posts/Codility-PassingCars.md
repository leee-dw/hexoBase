---
title: 'Codility: PassingCars'
categories: Algorithm
date: 2018-05-19 23:50:01
tag: Codility
---
```javascript
function solution(A) {
  let count = 0;
  for (var i = 0; i < A.length; i++) {
    for (var j = 1; j < A.length; j++) {
      if (i < j && A[i] < A[j]) {
        count++;
      }
    }
  }
  return count
}

```

https://app.codility.com/demo/results/trainingBJU44R-VSM/