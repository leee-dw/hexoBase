---
title: 'HackerRank: Divisible Sum Pairs'
categories: Algorithm
date: 2018-08-17 16:07:34
tag:
---

```js
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var divider = Number(input[0].split(' ')[1]);
var list = input[1].split(' ').map(el => Number(el))
var count = 0;


for (var i = 0; i < list.length; i++) {
  for (var j = 0; j < i; j++) {
    (list[i] + list[j]) % divider === 0 && count++;
  }
}

console.log(count);
```


https://www.hackerrank.com/challenges/divisible-sum-pairs/submissions/code/81671562