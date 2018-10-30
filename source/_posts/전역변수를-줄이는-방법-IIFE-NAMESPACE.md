---
title: 전역변수를 줄이는 방법 (IIFE & NAMESPACE)
categories: Dev
date: 2018-01-17 11:26:17
tag: Javascript
---

자바스크립트 코딩을 하다보면 전역변수가 증가할 확률이 높아집니다. 
전역변수를 없애는 방법이 몇 가지 있는데, 대표적인 방법으로 즉시실행함수(IIFE)와 Namespace가 있습니다.

```javascript
var myText = "hello world";
const myArr = ["name", "hello world", 23];
function getName(name){
  return "youn" + name;
}
```

위의 코드는 모두 전역변수입니다. 이렇게 작성하면 나중에 유지보수하기 어렵고, 코드가 충돌할 확률이 높아집니다. 이를 해결하기 위해 함수를 그룹화하는 방법이 있습니다. 함수를 Grouping하면 외부에서의 접근이 어렵습니다. 

```javascript
(function (){
  var myText = "hello world";
  const myArr = ["name", "hello world", 23];
  function getName(name) {
    return "youn" + name;
  }
})();
```


자바스크립트는 변수의 유효범위가 `function` 단위이기 때문에, 어떤 특정 `function` 안에 존재할 경우 외부에서 접근이 불가능합니다. 다시 말해, 위의 코드는 전역변수가 아니라 지역변수가 된 것이고, 함수 안에서만 변수를 사용한다고 가정했을 때에는 함수 안에서 표현해서 그 안에서 모든 처리가 끝나게 됩니다. 이렇게 되면 전역변수가 없어지니 함수 밖에서 `myText`변수나  `myArr` 상수에 접근할 수 없습니다. 이를 *캡슐화* 했다고 말하기도 합니다. 함수의 마지막 코드에는 괄호를 열고 닫는 것 코드가 있는데, 이 괄호의 의미는 함수를 바로 실행한다는 뜻입니다. 
이를 *즉시실행함수* 라고 합니다.


전역변수를 없애는 또 다른 방법은 다음과 같습니다. 

```javascript
var story = {};
story.getName = function(name) {
  return "youn" + name;
}
story.setName = function(name) {
  this.name = name;
}
```

```javascript
var story = {};
story.name = "jisu";
story.getName = function() {};
```

위의 코드처럼 작성하면 `story`라는 객체만 생겼고, 함수가 아무리 증가해도 `namespace`는 한 개만 유지할 수 있습니다. 
```javascript
story.manager = {};  // Object {}
```



complexed hierarchy 관계를 만들고 싶다면, 아래와 같이 입력할 수 있습니다.
```javascript
story.manager.getName = function () {}; // function () {}
```


위 코드를 부르고 싶다면 아래와 같이 입력할 수 있습니다.
```javascript
story.manager.getName(); // undefined
```

이를 NameSpace Pattern이라고 부릅니다.


{% callout info %}
#### {% fa info-circle %} 위 포스팅은 [코드스쿼드](http://codesquad.kr/) [윤지수 마스터님](https://github.com/nigayo)의 강의를 참고했습니다.
{% endcallout %}
