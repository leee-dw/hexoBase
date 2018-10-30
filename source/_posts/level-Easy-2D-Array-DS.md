---
title: level Easy. 2D Array DS
categories: Algorithm
date: 2017-12-15 23:57:16
---
출처: https://www.hackerrank.com/challenges/2d-array/problem

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var arr = input[0].split(' ')
var arr = [];

for (var i = 0; i < input.length - 2; i++) {
  for (var j = 0; j < input.length - 2; j++) {
    var hourglass =
      Number(input[i].split(' ')[j]) + Number(input[i].split(' ')[j + 1]) + Number(input[i].split(' ')[j + 2]) + Number(input[i + 1].split(' ')[j + 1]) + Number(input[i + 2].split(' ')[j]) + Number(input[i + 2].split(' ')[j + 1]) + Number(input[i + 2].split(' ')[j + 2])
    arr.push(hourglass);
  }
}

var max = Math.max.apply(null, arr);
console.log(max);
```

시간이 걸렸지만 문제가 어렵진 않았다.
