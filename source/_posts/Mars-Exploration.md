---
title: Mars Exploration
categories: Algorithm
date: 2018-03-27 12:08:30
---

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString()
var arr = [];
var res = [];
var count = 0;
for (var i = 0; i < input.length; i += 3) {
  arr.push(input.substring(i, i + 3));
}

for (var i = 0; i < arr.length; i++) {
  res.push(arr[i].split(''));
}

for (var i = 0; i < res.length; i++) {
  if (res[i][0] !== 'S') {
    count++;
  }
  if (res[i][1] !== 'O') {
    count++;
  }
  if (res[i][2] !== 'S') {
    count++;
  }
}

console.log(count);
```

> 출처: https://www.hackerrank.com/challenges/mars-exploration/problem