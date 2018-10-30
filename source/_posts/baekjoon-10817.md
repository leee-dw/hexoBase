---
title: 'baekjoon: 10817'
categories: Algorithm
date: 2018-01-06 21:57:46
---


출처: https://www.acmicpc.net/problem/10817

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split(' ');
var arr =[]; 

for (var i = 0; i < input.length; i++) {
  arr.push(Number(input[i]))
}


if (arr[0] >= arr[1] && arr[1] >= arr[2]) {
  console.log(Number(arr[1]));
} else if (arr[0] >= arr[2] && arr[2] >= arr[1]) {
  console.log(Number(arr[2]));
} else if (arr[1] >= arr[0] && arr[0] >= arr[2]) {
  console.log(Number(arr[0]));
} else if (arr[1] >= arr[2] && arr[2] >= arr[0]) {
  console.log(Number(arr[2]));
} else if (arr[2] >= arr[0] && arr[0] >= arr[1]) {
  console.log(Number(arr[0]));
} else if (arr[2] >= arr[1] && arr[1] >= arr[0]) {
  console.log(Number(arr[1]));
}
```

귀찮아서 대충 했다.