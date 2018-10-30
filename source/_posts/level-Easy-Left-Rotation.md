---
title: level Easy. Left Rotation
categories: Algorithm
date: 2017-12-15 23:59:11
---
출처: https://www.hackerrank.com/challenges/array-left-rotation/problem

## 나의 풀이

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var length = input[0].split(' ')[0];
var rotateNum = input[0].split(' ')[1];
var array = input[1].split(' ');
var storeArr, numArr = [];


for (var i = 0; i < array.length; i++) {
  numArr.push(Number(array[i]));
}

for (var j = 1; j <= rotateNum; j++) {
  storeArr = numArr.shift();
  numArr.push(storeArr);
}

console.log(numArr.join(' '));
```

string을 number로 바꾸지 않고 실행했을 때 메모리를 너무 많이 잡아먹는다. 
이걸 몰라서 한참을 헤맸다.