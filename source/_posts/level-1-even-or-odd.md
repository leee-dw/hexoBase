---
title: level 1. 짝수와 홀수
categories: Algorithm
date: 2017-12-07 21:39:34
---
## 문제
evenOrOdd 메소드는 int형 num을 매개변수로 받습니다. num이 짝수일 경우 "Even"을 반환하고 홀수인 경우 "Odd"를 반환하도록 evenOrOdd에 코드를 작성해 보세요. num은 0이상의 정수이며, num이 음수인 경우는 없습니다.
출처 : https://programmers.co.kr/learn/challenge_codes/122


### 내 풀이
```javascript
function evenOrOdd(num) {
  var result = ''
  if ( num % 2 === 0) {return "Even"} else {return "Odd"}
}
```



다음을```javascript
function evenOrOdd(num) {
  return (num % 2)? "Odd":"Even";
}
```



### 배운 점
컴퓨터는 1과 0으로 true, false를 인식한다.
알면서도 까먹고 있었구나 ㅠㅠ 삼항 연산자도 열심히 써먹자.
