---
title: 'baekjoon: 10869'
categories: Algorithm
date: 2018-02-03 03:47:11
---

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split(' ');
var arr = input.map(function (elem) {
  return Number(elem);
})

console.log(arr[0] + arr[1]);
console.log(arr[0] - arr[1]);
console.log(arr[0] * arr[1]);
console.log(parseInt(arr[0] / arr[1]));
console.log(arr[0] % arr[1]);
```