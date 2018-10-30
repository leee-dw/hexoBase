---
title: level 1. 수박수박수박수박수?
categories: Algorithm
date: 2017-12-07 21:45:54
---

## 문제
water_melon함수는 정수 n을 매개변수로 입력받습니다.
길이가 n이고, 수박수박수...와 같은 패턴을 유지하는 문자열을 리턴하도록 함수를 완성하세요.
예를들어 n이 4이면 '수박수박'을 리턴하고 3이라면 '수박수'를 리턴하면 됩니다.
출처: https://programmers.co.kr/learn/challenge_codes/109

합
### 나의 풀이

```javascript
function waterMelon(n) {
  var result = "";
  var word = '수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수박수';
  return word.slice(0, n);
}

// 실행을 위한 테스트코드입니다.
console.log("n이 3인 경우: " + waterMelon(3))
console.log("n이 4인 경우: " + waterMelon(4))
```

word 변수를 정의한 뒤, `slice` 메소드를 사용하여 첫번째 줄 부터 n 번째 줄까지 slice했다.
