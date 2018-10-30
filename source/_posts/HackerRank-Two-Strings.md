---
title: 'HackerRank: Two Strings'
categories: Algorithm
date: 2018-08-02 14:13:32
tag:
---

```js
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
input.shift();
var arr = input.map(elem => elem.split(''));

for (var i = 0; i < arr.length; i += 2) {
  var difference = [...new Set([...arr[i]].filter(x => new Set(arr[i + 1]).has(x)))];
  difference == '' ? console.log("NO") : console.log("YES")
}
```


https://www.hackerrank.com/challenges/two-strings/submissions/code/80043226

TIME OUT