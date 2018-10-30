---
title: level 2. 이상한 문자만들기
categories: Algorithm
date: 2017-12-17 19:14:09
---
출처: https://programmers.co.kr/learn/challenge_codes/114

### 나의 풀이 2017-12-17
```javascript
function toWeirdCase(s) {
  var arr = s.split(' ');
  // console.log(arr);
  var sentence = [];
  var result = [];


  for (var i = 0; i < arr.length; i++) {
    var word = arr[i].split('');
    for (var j = 0; j < word.length; j++) {
      if (j % 2 === 0) {
        result.push(word[j].toUpperCase());
      } else {
        result.push(word[j].toLowerCase());
      }
    }
  }
  console.log(result.join(''));
}


// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log("결과 : " + toWeirdCase("try hello world"));
```

결국 못품. 아... 짜증


### 나의 풀이 2017-12-18
```javascript
function toWeirdCase(s) {
  var arr = s.split(' ');
  var result = [];

  for (var i = 0; i < arr.length; i++) {
    var word = arr[i].split('');
    for (var j = 0; j < word.length; j++) {
      if (j % 2 === 0) {
        result.push(word[j].toUpperCase());
      } else {
        result.push(word[j].toLowerCase());
      }
    }
    result.push(" ");
  }
  return result.join('').trim();
}


// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log("결과 : " + toWeirdCase("try hello world"));
```

`reuslt.push(" ")` 을 쓰고, return 값에 `.trim()` 을 넣으니 해결됐다. 아오...


### 다른 사람의 풀이
```javascript
function toWeirdCase(s){
  //함수를 완성해주세요
  return s.toUpperCase().replace(/(\w)(\w)/g, function(a){
    return a[0].toUpperCase()+a[1].toLowerCase();
  })
}
```
무슨 풀이인지 모르겠다.