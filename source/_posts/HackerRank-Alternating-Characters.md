---
title: 'HackerRank: Alternating Characters'
categories: Algorithm
date: 2018-08-07 15:39:40
tag:
---

```js
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var lists = input.splice(1)
var count = 0;
var arr = lists.map(el => el.split(''));

for (var i = 0; i < arr.length; i++) {
  count = 0;
  for (var j = 1; j < arr[i].length; j++) {
    arr[i][j - 1] == arr[i][j] && count++
  }
  console.log(count);
}
```

https://www.hackerrank.com/challenges/alternating-characters/problem