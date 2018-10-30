---
title: 'baekjoon: 2908'
categories: Algorithm
date: 2018-02-03 03:46:03
---

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split(' ');
if (Number(input[0].split('').reverse().join('')) > Number(input[1].split('').reverse().join(''))) {
  console.log(Number(input[0].split('').reverse().join('')));
} else {
  console.log(Number(input[1].split('').reverse().join('')));
}
```