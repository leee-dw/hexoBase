---
title: 'Codility: CyclicRotation'
categories: Algorithm
date: 2018-04-27 16:54:46
tag: Codility
---
```js
function solution(A, K) {
  for (var i = 1; i <= K; i++) {
    A.unshift(A.pop())
  }
  return A;
}
```