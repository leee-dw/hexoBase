---
title: level 1. 역삼각형 출력하기
categories: Algorithm
date: 2017-12-07 21:43:48
---
## 문제
printReversedTriangle 메소드는 양의 정수 num을 매개변수로 입력받습니다.
다음을 참고해 `*`(별)로 높이가 num인 삼각형을 문자열로 리턴하는 printReversedTriangle 메소드를 완성하세요

높이(num)가 3일때 다음과 같은 문자열을 리턴하면 됩니다.
```
***
**
*
```
출처: https://programmers.co.kr/learn/challenge_codes/113


### 나의 풀이

```javascript
function printReversedTriangle(num) {
  var result = ''
  for (var i = num; i > 0; i--) {
    for (var j = 0; j < i; j++) {
      result += '*'
    }
    result += '\n'
  }
  return result
}

console.log("결과 : " + '\n' + printReversedTriangle(3));
```

이중반복문을 이용해서 풀었다. `result += '*'`가 생각나지 않아서 `result += i * '*'`를 썼고, 이게 안되서 다른 방법을 찾다가 30분을 헤맸다.

### 다른 사람의 풀이

```javascript
function printReversedTriangle(n) {
  return n > 0 ? '*'.repeat(n) + '\n' + printReversedTriangle(n-1) : '';
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log("결과 : " +'\n'+ printReversedTriangle(3));
```

`printReversedTriangle(n-1)` 뒤로 왜 계속 `*`이 생겨나는지 모르겠다. 좀 더 공부해야겠다...
