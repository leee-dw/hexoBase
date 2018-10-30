---
title: 'baekjoon: 15501'
categories: Algorithm
date: 2018-03-04 18:27:21
---

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var res = input[2].split(' ').join('')
var arr1 = input[1].split(' ');
var arr2 = input[1].split(' ').reverse();

var temp1;
var temp2;
var com = [];

for (var i = 0; i < arr1.length; i++) {
  temp1 = arr1.pop();
  temp2 = arr2.pop();

  arr1.unshift(temp1);
  arr2.unshift(temp2);

  com.push(arr1.join(''));
  com.push(arr2.join(''));
};

if (com.indexOf(res) !== -1) {
  console.log("good puzzle")
} else {
  console.log("bad puzzle")
}
```

자꾸 시간초과가 떠서 포기했다. 시간복잡도 이정도면 괜찮지 않나 ㅠㅠ