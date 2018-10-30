---
title: level 1. 평균 구하기
categories: Algorithm
date: 2017-12-07 21:45:19
---
## 문제 

함수를 완성해서 매개변수 list의 평균값을 return하도록 만들어 보세요.
어떠한 크기의 list가 와도 평균값을 구할 수 있어야 합니다.
출처: https://programmers.co.kr/learn/challenge_codes/126



### 나의 풀이

```javascript
function average(list) {
  //함수를 완성하세요
  var sum = 0;
  for (var i = 0; i < list.length; i++) {
    sum += list[i];
  }
  return sum / list.length;
}


// 아래는 테스트로 출력해 보기 위한 코드입니다.
var testArray = [5,3,4]
console.log("평균값 : " + average(testArray));
```
for 반복문을 돌려 나오는 값을 sum에 저장해 더했고, sum을 list.length로 나눴다.



### 다른 사람의 풀이

```javascript
function average(array){
  return array.reduce((a, b) => a + b) / array.length;
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
var testArray = [5,3,4] 
console.log("평균값 : " + average(testArray));
```

Arrow Function을 사용한 풀이를 발견했다.
reduce 메서드의 사용법이 무엇인지 찾아봐야겠다.