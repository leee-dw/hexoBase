---
title: Sequence Equation
categories: Algorithm
date: 2018-02-28 12:30:33
---

```javascript
var input =require('fs').readFileSync('/dev/stdin').toString().split('\n');

var p = input[1].split(' ').map(elem => {
  return Number(elem);
})

p.unshift(0);

for (var i = 1 ; i < p.length; i++) {
  for (var j = 1; j < p.length; j++) {
    if (i === p[p[j]]) {
      console.log(j);
    }
  }
}
```