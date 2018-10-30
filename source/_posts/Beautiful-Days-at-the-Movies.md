---
title: Beautiful Days at the Movies
categories: Algorithm
date: 2018-02-28 12:30:17
---

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split(' ');
var available = [];
var count = 0;
for (var i = Number(input[0]); i <= Number(input[1]); i++) {
  available.push(i);
}

for (var i = 0; i < available.length; i++) {
  if (Math.abs(available[i] - Number(available[i].toString().split('').reverse().join(''))) % input[2] === 0) {
    count++;
  }
}

console.log(count);

```