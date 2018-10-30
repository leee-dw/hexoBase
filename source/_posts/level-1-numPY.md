---
title: level 1. 문자열 내 p와 y의 개수
categories: Algorithm
date: 2017-12-08 12:20:50
---

## 문제
numPY함수는 대문자와 소문자가 섞여있는 문자열 s를 매개변수로 입력받습니다.
s에 'p'의 개수와 'y'의 개수를 비교해 같으면 True, 다르면 False를 리턴하도록 함수를 완성하세요. 'p', 'y' 모두 하나도 없는 경우는 항상 True를 리턴합니다.
예를들어 s가 "pPoooyY"면 True를 리턴하고 "Pyy"라면 False를 리턴합니다.

출처: https://programmers.co.kr/learn/challenge_codes/96

## 나의 풀이

```javascript
function numPY(s){
  var upCase = s.toUpperCase();
  // console.log(upCase);
  if (upCase.match(/P/g).length === upCase.match(/Y/g).length || !upCase.match(/Y/g) || !upCase.match(/P/g)) {
    return true
  } else if (upCase.match(/P/g).length !== upCase.match(/Y/g).length) {
     return false
  }
}


// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log( numPY("pPoooyY") )
console.log( numPY("Pyy") )
```

s 문자열을 모두 대문자로 바꾼 뒤, `.match()` 메소드를 사용했다. p의 길이와 y의 길이를 비교해 같다면 true를 리턴하거나, y 또는 p가 없다면 true를 리턴한다. p의 길이와 y의 길이를 비교해 같지 않다면  false를 리턴한다.


## 다른 사람의 풀이
```javascript
function numPY(s){
  var result = true;
  //함수를 완성하세요
    var b = 0;
  var c=0;
  for(var a=0;a<=s.length;a++){
        if(s.substring(a,a+1)=="p" ||s.substring(a,a+1)=="P"){
      b+=1;
      }else if(s.substring(a,a+1)=="y" || s.substring(a,a+1)=="Y"){
      c+=1;
      }


    if(b!=c){
    result=false;
    }else{
    result=true;
    }


  }
  console.log(b);
        console.log(c);

  return result;
}


// 아래는 테스트로 출력해 보기 위한 코드입니다.
console.log( numPY("pPoooyY") )
console.log( numPY("Pyy") )```
```

정규표현식을 사용하지 않고 문제를 푼 사람의 코드를 봤다. 신기했다.