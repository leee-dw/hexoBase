---
title: level 2. 콜라츠 추측
categories: Algorithm
date: 2017-12-08 11:51:13
---

## 문제
1937년 Collatz란 사람에 의해 제기된 이 추측은, 입력된 수가 짝수라면 2로 나누고, 홀수라면 3을 곱하고 1을 더한 다음, 결과로 나온 수에 같은 작업을 1이 될 때까지 반복할 경우 모든 수가 1이 된다는 추측입니다. 예를 들어, 입력된 수가 6이라면 6→3→10→5→16→8→4→2→1 이 되어 총 8번 만에 1이 됩니다. collatz 함수를 만들어 입력된 수가 몇 번 만에 1이 되는지 반환해 주세요. 단, 500번을 반복해도 1이 되지 않는다면 –1을 반환해 주세요.

출처: https://programmers.co.kr/learn/challenge_codes/15

### 나의 풀이
```javascript
function collatz(num) {
  var arr = [num];


  for (var i = 0; i <= 500; i++) {
    arr[i] % 2 === 0 ? arr.push(arr[i] / 2) : arr.push(arr[i] * 3 + 1);
    if (arr.indexOf(1)===i) {
      return i
    }
    }
  };

  // 아래는 테스트로 출력해 보기 위한 코드입니다.
  console.log(collatz(6));
  ```
짝수일 때, 2로 나누고, 홀수일때 3을 곱한 뒤 1을 더한 값을 배열에 넣어줬다. 그리고 입력된 수가 몇번 만에 1이 되는지 까지 구했는데,,, 500번을 반복해도 1이 되지 않는다면 -1을 반환해주는 걸 못해서 못풀었다. ㅠㅠ 나중에 다시 도전



## 2017-12-13 업데이트

### 나의 풀이
```javascript
function collatz(num) {
  var arr = [num];
  var maxNumber = 500;
  for (var i = 0; i < maxNumber; i++) {
    arr[i] % 2 === 0 ? arr.push(arr[i] / 2) : arr.push((arr[i] * 3) + 1);
    if (arr.indexOf(1) === i) {
      return i
    }
  }
  return -1
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log(collatz(6));
```
collatz 함수 마지막 줄에 -1을 리턴하면 끝나는 건데, 너무 헤맸다. 엉엉 ㅠㅠ


### 다른사람의 풀이
```javascript
function collatz(num,count = 0) {
    return num == 1 ? (count >= 500 ? -1 : count) : collatz(num % 2 == 0 ? num / 2 : num * 3 + 1,++count);
}

// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log( collatz(6) );
```
삼항식을 3번 사용해서 한 줄로 끝냈다. 