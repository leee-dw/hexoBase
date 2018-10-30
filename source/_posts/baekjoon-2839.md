---
title: 'baekjoon: 2839'
categories: Algorithm
date: 2018-01-02 22:24:43
---

출처: https://www.acmicpc.net/problem/2839

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString();


function answer() {
  for (var i = input; i < 5000; i++) {
    if (i == 3 || i == 5) {
      return 1;
    } else if (i == 4 || i == 7) {
      return -1;
    } else if (i % 5 === 0) {
      return (i / 5);
    } else if (i % 5 === 1) {
      return ((i - (3 * 2)) / 5) + 2;
    } else if (i % 5 === 2) {
      return ((i - (3 * 4)) / 5) + 4;
    } else if (i % 5 === 3) {
      return ((i - (3 * 1)) / 5) + 1;
    } else if (i % 5 === 4) {
      return ((i - (3 * 3)) / 5) + 3;
    }
  }
}

console.log(answer(input));
```