---
title: Cats and a Mouse
categories: Algorithm
date: 2018-02-22 14:58:30
---
```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var arr = [];
var test = [];
for (var i = 0; i < input.length; i++) {
  arr.push(input[i]);
};

for (var i = 1; i < arr.length; i++) {
  test.push(arr[i].split(' '));
};


for (var i = 0; i < test.length; i++) {
  if (Math.abs(test[i][2] - test[i][0]) > Math.abs(test[i][2] - test[i][1])) {
    console.log("Cat B");
  } else if (Math.abs(test[i][2] - test[i][0]) < Math.abs(test[i][2] - test[i][1])) {
    console.log("Cat A");
  } else {
    console.log("Mouse C")
  }
}
```