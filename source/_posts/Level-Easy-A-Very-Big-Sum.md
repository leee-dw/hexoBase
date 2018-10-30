---
title: Level Easy. A Very Big Sum
categories: Algorithm
date: 2017-12-18 23:55:59
---
출처: https://www.hackerrank.com/challenges/a-very-big-sum/problem


## 나의 풀이
```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var idx = input[1].split(' ')
var sum = 0;

for (var i = 0; i <= idx.length - 1 ; i++) {
  sum += Number(idx[i]);
}

console.log(sum);
```

1분만에 간단하게 풀린 것 같다.