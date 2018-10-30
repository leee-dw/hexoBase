---
title: level 3. 야근 지수
categories: Algorithm
date: 2018-02-27 13:24:52
---

```javascript
function noOvertime(no, works) {
  var sum = 0;

  for (var i = 0; i < no; i++) {
    works.sort(function (a, b) {
      return a - b;
    });
    works[works.length - 1] -= 1;
  }
  works.forEach(element => {
    sum += Math.pow(element, 2);
  });
  return sum
}
```

출처: https://programmers.co.kr/learn/challenge_codes/27