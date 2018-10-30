---
title: level 3. N개의 최소공배수
categories: Algorithm
date: 2018-02-27 13:22:17
---
```javascript
function nlcm(num) {
  var bigger = num.sort((a, b) => {
    return a - b;
  })[num.length - 1];

  while (true) {
    if (bigger % num[0] === 0 &&
      bigger % num[1] === 0 &&
      bigger % num[2] === 0 &&
      bigger % num[3] === 0 &&
      bigger % num[4] === 0 &&
      bigger % num[5] === 0 &&
      bigger % num[6] === 0 &&
      bigger % num[7] === 0 &&
      bigger % num[8] === 0 &&
      bigger % num[9] === 0) {
      return bigger
    }
    bigger++;
  }
}
```

출처: https://programmers.co.kr/learn/challenge_codes/152