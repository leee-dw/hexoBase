---
title: level Easy. Reverse Integer
categories: Algorithm
date: 2017-12-20 00:13:41
---


출처: https://leetcode.com/problems/reverse-integer/description/

## 나의 풀이
```javascript

var reverse = function (x) {
var str = x + ""
var arr = str.split('');
var reverse = [];


for (var i = 1 ; i <= arr.length; i++) {
  reverse.push(arr[arr.length - i])
}

    if (reverse.length >= 10 && reverse[reverse.length - 1] == "-" || reverse.length >= 10) {
        return 0;
    } else if(reverse[reverse.length - 1] === "-") {
        reverse.pop();
        return Number(reverse.join(''))*-1;
    } else {
        return Number(reverse.join(''));
    }
}
```

아. 통과가 안된다... 