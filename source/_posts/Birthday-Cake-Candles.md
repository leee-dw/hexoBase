---
title: Birthday Cake Candles
categories: Algorithm
date: 2018-02-01 17:01:21
---

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var arr = input[1].split(' ').map(elem => {
  return Number(elem);
})

arr.sort(function (a, b) {
  return a - b;
});


var result = {};
var res = [];

for (var val of arr) {
  result[val] = result[val] == undefined ? 1 : result[val] += 1;
}

for (var value in result) {
  res.push(result[value]);
}

console.log(Math.max.apply(null, res));
```