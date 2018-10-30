---
title: Level Easy. Plus Minus
categories: Algorithm
date: 2017-12-20 23:47:49
---
출처: https://www.hackerrank.com/challenges/plus-minus/problem

### 나의 풀이

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n')
var length = input[0];
var inputs = input[1].split(' ');
var nums = [];

var plus = [];
var minus = [];
var zero = [];

for (var i = 0; i < inputs.length; i++) {
  nums.push(Number(inputs[i]));
  if (nums[i] > 0) {
    plus.push(i)
  } else if (nums[i] < 0) {
    minus.push(i)
  } else {
    zero.push(i)
  }
}

console.log((plus.length / length).toFixed(6));
console.log((minus.length / length).toFixed(6));
console.log((zero.length / length).toFixed(6));
```

1. 양수, 음수, 0에 대한 각 배열을 생성한 뒤 `.push()`로 넣어 준다.
2. `.toFixed()` 메서드를 사용해 자릿값에 맞게 변환한 뒤 `console.log` 출력
