---
title: 'baekjoon: 1157'
categories: Algorithm
date: 2018-02-03 03:44:35
---

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().toUpperCase().split('').sort();
var res = {};

for (var value in input) {
  var index = input[value];
  res[index] = res[index] === undefined ? 1 : res[index] += 1
};

var arr = [];
for (var val in res) {
  arr.push(res[val]);
  arr.sort(function (a, b) {
    return b - a;
  });
}

var ans = '';
for (var val in res) {
  if (arr[0] === res[val] && arr[0] > arr[1]) {
    ans = val.toUpperCase();
  }
}

if (ans === '') {
  console.log("?");
} else {
  console.log(ans);
}
```