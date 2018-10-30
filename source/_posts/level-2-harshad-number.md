---
title: level 2. 하샤드 수
categories: Algorithm
date: 2017-12-07 21:57:55
---

## 문제

양의 정수 x가 하샤드 수이려면 x의 자릿수의 합으로 x가 나누어져야 합니다. 예를들어 18의 자릿수 합은 1+8=9이고, 18은 9로 나누어 떨어지므로 18은 하샤드 수입니다.

Harshad함수는 양의 정수 n을 매개변수로 입력받습니다. 이 n이 하샤드수인지 아닌지 판단하는 함수를 완성하세요.
예를들어 n이 10, 12, 18이면 True를 리턴 11, 13이면 False를 리턴하면 됩니다.

출처: https://programmers.co.kr/learn/challenge_codes/129

### 나의 풀이

```javascript
function Harshad(n) {
  var numStr = n.toString();
  var numDigit = numStr.length;
  var sum = 0;

  for (var i = numDigit; i > 0 ; i--) {
    sum += Math.floor(n % Math.pow(10, i) / Math.pow(10, i - 1))
  }
  if (n % sum === 0) {
    return true
  } else {
    return false
  }
}

console.log(Harshad(18))
```

숫자를 문자열로 바꾼 뒤, 몇자리 수인지 알아내기 위해 문자열의 길이값을 구했다.
`Math.pow()` 메서드를 사용해서 자리수에 대해 알아냈고, 각 자리수의 값을 구하기 위해 `Math.floor(n % Math.pow(10, i) / Math.pow(10, i - 1)` 를 사용했다. 그리고 sum에 위에서 나온 각각의 값을 더했다. Harshad(n)의 값이 sum으로 나누었을 때 나머지가 0이라면 true를 반환하도록 조건문을 썼다.


### 다른 사람의 풀이
```javascript
function Harshad(n){
  return !(n%(n+'').split('').reduce(function (i, sum) {return +sum + +i;}));
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(Harshad(18))
```

split을 사용해서 문제를 해결한 사람들이 많았다. 존경...reduce는 어떻게 쓰는거지...