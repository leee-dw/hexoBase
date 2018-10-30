---
title: 'Programmers L1 : 두 정수 사이의 합'
categories: Algorithm
date: 2018-09-12 11:59:15
tag:
---
```js
function solution(a, b) {
  let arr = [];
  let sum = 0;
  if (a === b) return a;

  if (a < b) {
    for (var i = a; i <= b; i++) {
      sum += i;
    }
  } else {
    for (var i = b; i <= a; i++) {
      sum += i;
    }
  }
  return sum
}
```