---
title: 'baekjoon: 2748'
categories: Algorithm
date: 2018-03-07 10:27:44
---

```javascript
var input = Number(require('fs').readFileSync('/dev/stdin').toString());

function fibonacci(num) {
  return num === 1 || num === 2 ? 1 : fibonacci(num - 1) + fibonacci(num - 2);
}

console.log(fibonacci(input));
```

시간초과.