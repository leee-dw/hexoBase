---
title: 'HackerRank: Left Rotation'
categories: Algorithm
date: 2018-08-10 14:02:00
tag:
---

```js
let input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
let count = input[0].split(' ')[1], arr = input[1].split(' ');
console.log(arr.splice(count).concat(arr.slice(0, count)).join(' '));
```

https://www.hackerrank.com/challenges/ctci-array-left-rotation/submissions/code/80917549