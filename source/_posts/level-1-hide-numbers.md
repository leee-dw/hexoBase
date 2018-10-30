---
title: level 1. 핸드폰번호 가리기
categories: Algorithm
date: 2017-12-07 21:51:15
---

## 문제
별이는 헬로월드텔레콤에서 고지서를 보내는 일을 하고 있습니다. 개인정보 보호를 위해 고객들의 전화번호는 맨 뒷자리 4자리를 제외한 나머지를 `*`으로 바꿔야 합니다.
전화번호를 문자열 s로 입력받는 hide_numbers함수를 완성해 별이를 도와주세요
예를들어 s가 "01033334444"면 `*******4444`를 리턴하고, "027778888"인 경우는 `*****8888`을 리턴하면 됩니다.

출처: https://programmers.co.kr/learn/challenge_codes/132


### 나의 풀이

```javascript
function hide_numbers(s){
  var backNum = s.slice(s.length - 4, s.length)
  var frontNum = s.slice(0, s.length - 5)
  var star = frontNum.replace(/[0-9]/g, '*') + '*'
  var answer =  star + backNum  

  return answer;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log("결과 : " + hide_numbers('01033334444'));
```

아 ㅋㅋㅋㅋㅋ 내가 봐도 너무 망나니처럼 풀었다.

### 나의 풀이: 2017-12-18
```javascript
function hide_numbers(s){
  var result = ""
  var frontNum = s.slice(0, s.length-4);
  var backNum = s.slice(s.length-4, s.length);
  for (var i = 0; i<frontNum.length; i++) {
    result += "*" 
  }
  return result+backNum;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log("결과 : " + hide_numbers('01033334444'));
```

for loop 를 이용해서 풀었다. 해결.