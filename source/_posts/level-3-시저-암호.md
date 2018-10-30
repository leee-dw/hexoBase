---
title: level 3. 시저 암호
categories: Algorithm
date: 2018-02-27 13:23:02
---

```javascript
function caesar(s, n) {
  var arr = s.split('');
  var res = [];
  var ans = [];
  var answer = [];

  for (var i = 0; i < arr.length; i++) {
    res.push(arr[i].charCodeAt(0));
    if (n > 26) {
      var N = n - 26;
    }
    if (res[i] + N > 90 && res[i] <= 90) {
      ans.push(res[i] - 26 + N);
    } else if (res[i] + N > 122 && res[i] <= 122) {
      ans.push(res[i] - 26 + N);
    } else {
      ans.push(res[i] + N);
    }
  }
  for (var i = 0; i < ans.length; i++) {
    if (ans[i] <= 64) {
      ans[i] = 32;
    }
    answer.push(String.fromCharCode(ans[i]));
  }
  return answer.join('').replace(/2/g, " ");
}

// 실행을 위한 테스트코드입니다.
console.log(caesar("i oOUnORgEcjkwBYLfBnxRBQolzPmfQbklmU wF bvTZRixBEY", 41));
```

출처: https://programmers.co.kr/learn/challenge_codes/144