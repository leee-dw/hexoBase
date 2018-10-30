---
title: 'Codility: BinaryGap'
categories: Algorithm
date: 2018-03-28 13:25:26
tag: Codility
---

```javascript
function solution(N) {
  var source = N.toString(2)
  var flag;
  var temp = 0;
  var res = [];

  for (var elem of source) {
    if (elem === '0') {
      flag = true;
    }

    if (flag) {
      temp += 1;
    }

    if (elem === '1') {
      flag = false;
      res.push(temp);
      temp = 0;
    }
  }
  return Math.max(...res) === 0 ? Math.max(...res) : Math.max(...res) - 1
```

https://app.codility.com/demo/results/training2QYHFA-GXP/