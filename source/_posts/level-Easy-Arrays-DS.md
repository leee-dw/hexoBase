---
title: level Easy. Arrays DS
categories: Algorithm
date: 2017-12-15 15:09:24
---
출처: https://www.hackerrank.com/challenges/arrays-ds/problem

##나의 풀이

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');

var length = Number(input[0]) - 1
var arr = input[1].split(' ');
var newArr = [];

for (var i = 0; i <= length; i++) {
  newArr.push(Number(arr[length - i]));
}
  console.log(newArr.join(' '));
```

기존 배열의 마지막 인자부터 역순으로 새로운 배열에 담아서 문제를 풀었다.
처음엔 새로운 변수를 만들고 그 변수에 차례대로 담아 하노이의 탑 문제를 풀듯이 해결해보려 했지만, 배열이 홀수일 경우  문제가 발생해서 2시간 가량 고민을 했다. 