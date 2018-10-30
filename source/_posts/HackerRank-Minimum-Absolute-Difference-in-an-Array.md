---
title: 'HackerRank: Minimum Absolute Difference in an Array'
categories: Algorithm
date: 2018-08-09 18:05:58
tag:
---

```js
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var arr = input[1].split(' ').sort((a, b) => a - b);
var res = arr.map((el, idx) => arr[idx + 1] - arr[idx]);
res = res.filter(val => !!val);
console.log(Math.min(...res));
```

https://www.hackerrank.com/challenges/minimum-absolute-difference-in-an-array/submissions/code/80822001