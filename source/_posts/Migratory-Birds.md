---
title: Migratory Birds
categories: Algorithm
date: 2018-02-22 15:02:21
---


```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');

var arr = input[1].split(' ').map(function (elem) {
  return Number(elem);
}).sort((a, b) => {
  return a - b;
});

var res = {};
var ans = [];
var answer = [];

for (var val of arr) {
  res[val] = res[val] === undefined ? 1 : res[val] += 1;
}

for (var val in res) {
  ans.push(res[val]);
};

console.log(ans);

for (var i = 0; i < ans.length; i++) {
  if (Math.max.apply(null, ans) === ans[i]) {
    answer.push(i+1);
  }
}
```