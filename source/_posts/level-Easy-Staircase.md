---
title: level Easy. Staircase
categories: Algorithm
date: 2017-12-19 13:47:18
---
출처: https://www.hackerrank.com/challenges/staircase/problem

## 나의 풀이
```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var length = Number(input);
var stair = "";

for (var i = 0; i < length; i++) {
  stair = "";

  for (var j = length - 1; j > i; j--) {
    stair += " ";
  }
  for (var j = 0; j <= i; j++) {
    stair += "#";
  }
  console.log(stair);
}
```

허허..