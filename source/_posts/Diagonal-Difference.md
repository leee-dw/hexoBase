---
title: Diagonal Difference
categories: Algorithm
date: 2018-02-22 16:33:25
---

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var arr = [];
var answer = [];


for (var i = 1; i < input.length; i++) {
  arr.push(input[i].split(' '));
}

for (var i = 0; i < arr.length; i++) {
  var ans = [];
  for (var j = 0; j < arr[i].length; j++) {
    ans.push(Number(arr[i][j]));
  }
  answer.push(ans)
}

var sumA = 0;
var sumB = 0;
for (var i = 0; i < answer.length; i++) {
  for (var j = 0; j < answer.length; j++) {
    if (i === j) {
      sumA += answer[i][j];
      sumB += answer[i][answer.length - 1 - j];
    }
  }
}

console.log(Math.abs(sumA - sumB));
```