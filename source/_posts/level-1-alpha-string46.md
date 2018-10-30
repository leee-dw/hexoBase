---
title: level 1. 문자열 다루기 기본
categories: Algorithm
date: 2017-12-07 21:46:39
---
## 문제
alpha_string46함수는 문자열 s를 매개변수로 입력받습니다.
s의 길이가 4혹은 6이고, 숫자로만 구성되있는지 확인해주는 함수를 완성하세요.
예를들어 s가 "a234"이면 False를 리턴하고 "1234"라면 True를 리턴하면 됩니다
출처: https://programmers.co.kr/learn/challenge_codes/99

### 나의 풀이

```javascript
var res;

function alpha_string46(s) {

  if (s.length === 4 && s.replace(/[^0-9]/g,"") == s || s.length === 6 && s.replace(/[^0-9]/g,"") == s) {
    return true
  } else {
    return false
  }
}


// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(alpha_string46('a123'));```

s의 길이값을 비교하고, 
`s.length === 4 || s.length === 6`
s 문자열 안에 문자가 있을 경우 공백으로 처리하여, 숫자만 남겼다. 
그리고 `s.replace`를 s와 비교해서 같다면 true를 리턴하도록 하였고, 다르다면 false를 리턴하도록 설계했다.
가끔 오답이 나는데, 이유를 모르겠다.


### 다른 사람의 풀이

```javascript
function alpha_string46(s){
    return /^\d{4}(\d{2})?$/.test(s);
}
```
Honux의 풀이인데, 정규표현식을 이해하기 어렵다.
