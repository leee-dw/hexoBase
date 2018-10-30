---
title: level 3. 멀리 뛰기
categories: Algorithm
date: 2018-02-27 13:23:36
---

```javascript
const jumpCase = (num) => {
  return num === 0 || num === 1 ? 1 : jumpCase(num - 1) + jumpCase(num - 2);
}

console.log(jumpCase(4));
```

출처: https://programmers.co.kr/learn/challenge_codes/153