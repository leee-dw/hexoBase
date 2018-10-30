---
title: 'baekjoon: 2920'
categories: Algorithm
date: 2018-02-03 03:46:36
---

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString();
var arr = input.split(' ').map(function (elem) {
  return Number(elem);
});

var result = {};
var res = [];

for (var i = 1; i < arr.length; i++) {
  if (arr[i - 1] < arr[i]) {
    res.push("ascending")
  } else if (arr[i - 1] > arr[i]) {
    res.push("descending")
  }
}

for (var val in res) {
  var index = res[val];
  result[index] = result[index] == undefined ? 1 : result[index] += 1;
}


if (result[index] === 7) {
  console.log(index);
} else {
  console.log("mixed");
}
```