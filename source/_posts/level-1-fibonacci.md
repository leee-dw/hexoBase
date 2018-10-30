---
title: level 1. 피보나치 수
categories: Algorithm
date: 2017-12-07 21:47:53
---

## 문제

피보나치 수는 F(0) = 0, F(1) = 1일 때, 2 이상의 n에 대하여 F(n) = F(n-1) + F(n-2) 가 적용되는 점화식입니다. 2 이상의 n이 입력되었을 때, fibonacci 함수를 제작하여 n번째 피보나치 수를 반환해 주세요. 예를 들어 n = 3이라면 2를 반환해주면 됩니다.

- 출처: https://programmers.co.kr/learn/challenge_codes/6

### 나의 풀이

```javascript
function fibonacci(num) {
  var arr =[0, 1];
  for (var i = 2; i <= num; i++) {
    arr[i] = arr[i - 1] + arr[i - 2]
  }
  return arr[arr.length-1];
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(fibonacci(10))
```

반복문을 돌린 후, 마지막 배열 값을 추출하는 방법`a[a.length - 1]`으로 return하여 답을 찾았다. 

### 다른 사람들의 풀이

```javascript
var fibonacci = function (n) {
  return n < 2 ? n : fibonacci(n - 1) + fibonacci (n - 2);
};
```

프로그래머스에 올라온 풀이를 살펴보던 중 더글라스 크락포드 센세가 풀었던 코드가 생각나서 옮겨적었다. 삼항연산자를 사용한 방법이였는데, 어떻게 동작하는지 원리를 이해하지 못했다. 아, 이해했다.