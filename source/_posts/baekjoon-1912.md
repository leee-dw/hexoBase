---
title: 'baekjoon: 1912'
categories: Algorithm
date: 2018-02-01 17:03:17
---
```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var str = input[1].split(' ');
var arr = [];
var arr2 = [];
var res = [];

for (var i = 0; i < str.length; i++) {
  arr.push(Number(str[i]))
  arr2.push(Number(str[i]))
}


arr2.sort(function (a, b) {
  return a - b;
})

for (var i = 1; i < input[0]; i++) {

  res.push(arr[i] += arr[i - 1]);
}
console.log(res);

var max = Math.max.apply(null, res);



if (arr2[arr2.length - 1] > max) {
  console.log(arr2[arr2.length - 1]);
} else {
  console.log(max);
}
```

못 풀었다.