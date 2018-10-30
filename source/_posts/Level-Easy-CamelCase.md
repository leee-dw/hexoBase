---
title: Level Easy. CamelCase
categories: Algorithm
date: 2017-12-22 23:09:41
---
출처: https://www.hackerrank.com/challenges/camelcase/problem

### 나의 풀이

```javascript
var input = require('fs').readFileSync('/dev/stdin').toString().split('\n');
var camelCase = input[0].split('');
var div = [];
var ans =[];

for (var i = 0; i < camelCase.length; i++) {
  if (camelCase[i] === camelCase[i].toUpperCase()) {
    div.push(i)
  }
}

for (var i = 0; i< div.length; i++) {
ans.push(camelCase.slice(div[i], div[i+1]).join(''));
}

console.log(ans.length + 1);
```

쉽게 풀었다.