---
title: sum Two Smallest Numbers
categories: Algorithm
date: 2018-02-01 17:00:33
---
```javascript
function sumTwoSmallestNumbers(numbers) {
  var arr = numbers.sort((a, b) => {
    return a - b
  })
  console.log(arr[0] + arr[1]);
};
```