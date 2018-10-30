---
title: Tutorial intro
categories: Algorithm
date: 2018-03-27 12:09:18
---

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var arr = input[2].split(' ');
console.log(arr.indexOf(input[0]));
```

> 출처: https://www.hackerrank.com/challenges/tutorial-intro/problem