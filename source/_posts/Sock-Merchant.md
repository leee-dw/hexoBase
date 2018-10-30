---
title: Sock-Merchant
categories: Algorithm
date: 2018-02-22 14:59:18
---

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var arr = input[1].split(' ').map((elem) => {
  return Number(elem)
}).sort(function (a, b) {
  return a - b;
})

var res = {};
var count = 0;

for (var val of arr) {
  res[val] = res[val] == undefined ? 1 : res[val] += 1;
}

for (var val in res) {
    count += Math.floor(res[val] / 2);
};

console.log(count);
```