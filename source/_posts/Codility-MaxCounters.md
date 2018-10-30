---
title: 'Codility: MaxCounters'
categories: Algorithm
date: 2018-03-28 13:25:42
tag: Codility
---

```javascript
const solution = (N, A) => {
  let a = [];
  let arr;

  for (let i = 0; i < N; i++) {
    a.push(i);
    arr = a.fill(0);
  }

  A.forEach(elem => {
    elem <= N ? arr[elem - 1] += 1 : arr.fill(Math.max(...arr));
  })
  return arr;
}
```

https://app.codility.com/demo/results/training8ECJ46-QD8/