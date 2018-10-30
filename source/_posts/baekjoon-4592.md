---
title: 'baekjoon: 4592'
categories: Algorithm
date: 2018-03-15 09:57:45
---

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var res = [];
var flag;
var tempString = '';
var str = '';

var arr = input.map(function (elem) {
  return elem.split(' ');
});

for (var i = 0; i < arr.length; i++) {
  arr[i].shift();
  for (var j = 0; j <= arr[i].length; j++) {
    if (arr[i][j] !== arr[i][j + 1]) {
      res.push(arr[i][j]);
    }
  }
  res.push("$");
}
 

res.forEach(function (elem) {
  flag = true;
  
  if (flag) {
    tempString += elem + " ";
  }

  if (elem === "$") {
    flag = false;
    str += tempString + '\n';
    tempString = '';
  }
});

console.log(str.slice(0, -5));
```