---
title: 'Codility: PermMissingElem'
categories: Algorithm
date: 2018-03-30 22:13:21
tag: Codility
---

```javascript
function solution(A) {
  var arr = A.sort(function (a, b) {
    return a - b;
  })

  for (var elem in arr) {
    if (arr[elem] !== Number(elem) + 1) {
      return Number(elem) + 1;
    }
  }
  return arr.length + 1
}
```

https://app.codility.com/demo/results/trainingQBX9Q4-8PN/