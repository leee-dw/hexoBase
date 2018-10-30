---
title: 'Codility: OddOccurrencesInArray'
categories: Algorithm
date: 2018-04-27 16:55:10
tag: Codility
---

```js
function solution(A) {
  var res = {};

  for (var idx of A) {
    res[idx] = res[idx] == undefined ? 1 : res[idx] += 1;
  }

  for (var value in res) {
    if (res[value] & 1) {
      return Number(value);
    }
  }
}
```