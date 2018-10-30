---
title: 2017-12-01- Algorithm
categories: Algorithm
date: 2017-12-01 23:24:00
---



## 임의의 난수를 생성해 봅시다.

- 풀이
```javascript
Math.random();
```

## 0 ~ 9 사이의 임의의 난수를 생성해 봅시다.

- 풀이
```javascript
let maxNumber = 100;
for (let num = 0; num < maxNumber; num++) {
  let random = Math.random() * 10;
  console.log(random);
}
```

## 0 ~ 9 사이의 임의의 정수를 생성해 봅시다.

- 풀이
```javascript
let maxNumber = 10;
for (let int = 1; int < maxNumber; int++) {
  let random = Math.floor(Math.random(int) * 10);
  console.log(random);
}
```


## 1 ~ 10 사이의 임의의 정수를 생성해 봅시다.

- 풀이
```javascript
let maxNumber = 10;
for (let int = 1; int < maxNumber; int++) {
  let random = Math.floor(Math.random(int) * 10) + 1;
  console.log(random);
}
```

## `2, 4, 6, 8, 10` 중 임의의 정수를 생성해 봅시다.

- 풀이

```javascript
let even = [2, 4, 6, 8, 10];
let randomInt = Math.floor(Math.random()*5);
console.log(even[randomInt]);
```


## 5에서 생성한 값을 변수 n에 담고 출력해 봅시다.

- 풀이

```javascript
let even = [2, 4, 6, 8, 10];
let randomInt = Math.floor(Math.random()*5);
let n = even[randomInt];
console.log(n);
```


## 다음과 같은 내용으로 10 이하의 임의의 홀수를 5번 출력하는 프로그램을 작성해 봅시다.

```
임의의 숫자 생성하는 프로그램
생성한 숫자는 5입니다.
생성한 숫자는 3입니다.
생성한 숫자는 7입니다.
생성한 숫자는 3입니다.
생성한 숫자는 5입니다.
```

- 풀이

```javascript
var odd = [1, 3, 5, 7, 9];
var randomNumber = Math.floor(Math.random()*11);
var maxNumber = 5;

for (var num = 1; num <= maxNumber; num++) {
  if (randomNumber === odd[num]) {
    console.log("생성한 숫자는 " + num + "입니다." );
  }
}
```

- 마지막 문제는 못풀었다. 처음 문제만 봤을 땐 쉽다고 생각했는데, 막상 문제를 풀어보려고 하니 생각보다 신경쓸 것도 많고, 시간도 많이 걸리고, 두뇌를 풀가동해도 문법이 내 마음대로 따라주지 않아 답답했다. 내일 다시 도전해봐야겠다.