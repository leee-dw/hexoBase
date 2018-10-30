---
title: 'Codility: FrogRiverOne'
categories: Algorithm
date: 2018-05-19 23:47:37
tag: Codility
---





```javascript
function solution(X, A) {
  const marks = new Set();
  return A.reduce((acc, crr, idx) => {
    crr <= X && marks.add(crr);
    return marks.size === X ? A.splice(1) && idx : acc;
  }, -1);
}
```

https://app.codility.com/demo/results/trainingWQMK4S-HCD/
