---
title: 'Codility: CountDiv'
categories: Algorithm
date: 2018-05-19 23:48:45
tag: Codility
---

```javascript
function solution(A, B, K) {
  return A !== B ? Math.ceil((B - A + 1) / K) : A % K === 0 ? 1 : 0;
}
```

https://app.codility.com/demo/results/trainingKQDQE6-QM8/