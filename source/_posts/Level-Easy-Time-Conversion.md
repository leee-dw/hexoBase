---
title: Level Easy. Time Conversion
categories: Algorithm
date: 2017-12-22 21:52:40
---

출처: https://www.hackerrank.com/challenges/time-conversion/problem

### 나의 풀이

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var arr = input[0].split(":");
var meridiem = arr[2].substring(2, 4);
var hour = Number(arr[0]);
var min = arr[1];
var sec = arr[2].split('').splice(0, 2).join('');


if (meridiem ==="PM" && hour === 12) {
  console.log(hour + ":" + min + ":" + sec);
} else if (meridiem ==="PM") {
  console.log(hour+ 12 + ":" + min + ":" + sec);
} else if (meridiem ==="AM" && hour === 12) {
  console.log("00" + ":" + min + ":" + sec);
} else if(hour < 10) {
  console.log("0" + hour + ":" + min + ":" + sec);
} else {
  console.log(hour + ":" + min + ":" + sec);
}
```

처음엔 이렇게까지 더럽게 풀 생각은 없었다...ㅎ