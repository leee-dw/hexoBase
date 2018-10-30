---
title: 'baekjoon: 10809'
categories: Algorithm
date: 2018-01-02 22:27:34
---

출처: https://www.acmicpc.net/problem/10809

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString();
var arr = [];
var alphabet = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'j', 'k', 'l', 'm', 'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z'];

for (var i = 0; i < alphabet.length; i++) {
  var loc = input.indexOf(alphabet[i]);
  arr.push(loc);
}

console.log(arr.join(" "));
```