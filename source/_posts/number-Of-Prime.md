---
title: number Of Prime
categories: Algorithm
date: 2018-02-06 11:50:53
---

```javascript
function numberOfPrime(n) {
  var arr = [];
  var primes = [];

  for (var i = 2; i <= n; ++i) {
    if (!arr[i]) {
      primes.push(i);
      for (var j = i <= 1; j <= n; j += i) {
        arr[j] = true;
      }
    }
  }
  return primes.length;
}

console.log(numberOfPrime(10));
```
