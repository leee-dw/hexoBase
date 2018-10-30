---
title: Electrics-Shop
categories: Algorithm
date: 2018-02-22 14:59:08
---

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var arr = [];
var keyboard = [];
var usb = [];
var sum = [];
var ans = [];
for (var i = 0; i < input.length; i++) {
  arr.push(input[i].split(' '));
}


for (var i = 0; i < arr[0][1]; i++) {
  keyboard.push(Number(arr[1][i]));
}


for (var i = 0; i < arr[0][2]; i++) {
  usb.push(Number(arr[2][i]));
}



for (var i = 0; i < keyboard.length; i++) {
  for (var j = 0; j < usb.length; j++) {
    sum.push(keyboard[i] + usb[j]);
  }
}

sum.sort(function (a, b) {
  return a - b;
})


if (sum[0] > Number(arr[0][0])) {
  console.log(-1)
} else {
  for (var i = 1; i < sum.length; i++) {
    if (sum[sum.length - i] <= Number(arr[0][0])) {
      ans.push(sum[sum.length - i]);
    }
  }

  ans.sort(function (a, b) {
    return a - b;
  })

  console.log(ans[ans.length - 1]);
}
```