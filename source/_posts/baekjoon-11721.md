---
title: 'baekjoon: 11721'
categories: Algorithm
date: 2018-01-29 17:22:26
---

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString();

for (var i = 0; i< input.length; i+=10) {
  console.log(input.slice(i, i + 10)); 
}
```
