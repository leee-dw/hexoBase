---
title: Level Medium. Sparse Arrays
categories: Algorithm
date: 2017-12-15 23:59:31
---
출처: https://www.hackerrank.com/challenges/sparse-arrays/problem

## 나의 풀이

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var findNum = input.join('').replace(/[^0-9]/g, " ").split(' ').filter(Number);
var arrNum = new Array;
var arrQ = new Array;
var arrA = new Array;


for (var i = 0; i < input.length; i++) {
  if (input[i] === findNum[0] || input[i] === findNum[1]) {
    arrNum.push(i)
  }
}

for (var i = 0; i < arrNum[1]; i++) {
  arrA.push(input[i])
}

for (var i = arrNum[1]; i < input.length; i++) {
  arrQ.push(input[i])
}
```

3~4시간 가량 고민했지만 결국 못풀었다. 휴