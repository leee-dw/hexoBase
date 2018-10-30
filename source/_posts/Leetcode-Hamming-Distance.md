---
title: 'Leetcode: Hamming Distance'
categories: Algorithm

date: 2018-06-06 18:31:16
tag: Leet Code
---
출처: https://leetcode.com/problems/hamming-distance/description/

```js
let hammingDistance = function (x, y) {
  let count = 0;
  let arrX = x.toString(2).split('');
  let arrY = y.toString(2).split('');

  for (let i = 0; i < arrX.length; i++) {
    if (arrX.length < 31) {
      arrX.unshift('0')
    }
  }

  for (let i = 0; i < arrY.length; i++) {
    if (arrY.length < 31) {
      arrY.unshift('0')
    }
  }

  for (let i = 0; i < 31; i++) {
    if (arrX[i] !== arrY[i]) {
      count++
    }
  }
  return count
};
```