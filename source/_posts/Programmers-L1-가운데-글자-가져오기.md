---
title: 'Programmers L1 : 가운데 글자 가져오기'
categories: Algorithm
date: 2018-09-12 11:57:13
tag:
---

```js
function solution(s) {
  let str = s.split('');
  if (str.length % 2) {
    return str[Math.ceil(str.length / 2) - 1]
  } else {
    return str[Math.ceil(str.length / 2) - 1] + str[Math.ceil(str.length / 2)]
  }
}
```

