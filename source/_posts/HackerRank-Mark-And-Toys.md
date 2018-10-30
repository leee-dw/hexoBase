---
title: 'HackerRank: Mark And Toys'
categories: Algorithm
date: 2018-08-07 15:12:01
tag:
---

```js
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var numberOfToys = input[0].split(' ')[0];
var money = input[0].split(' ')[1];
var toys = input[1].split(' ').sort((a, b) => a - b);
var count = 0;


for (var i = 0; i < numberOfToys; i++) {
  money -= toys[i];
  money > 0 && count++;
}

console.log(count);
```


https://www.hackerrank.com/challenges/mark-and-toys/problem