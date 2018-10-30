---
title: Arrow function vs. Function
categories: Dev
date: 2018-07-13 15:35:05
tag:
- Javascript
- ES6
---


​ Arrow function이 function과 달리 왜 this를 바인딩 하지 못하는지 공부하면서, Arrow function과 Function의 차이점에 대해 비교했다.
1. Arrow function는 항상 바인딩 된 this를 갖고 있기 때문에 this의 Scope를 바꿀 수 없다. 따라서 `.bind()`, `call()` 메서드 또한 사용할 수 없다. 

2. Arrow function은 `arguments` 키워드를 지원하지 않는다. ES6에서 사용중인 새로운 방식의 인수조작(기본 매개변수, 나머지 매개변수 등)으로 `arguments`로 했던 모든 기능들을 대체할 수 있기 때문에 더 이상 `arguments`는 필요가 없어졌기 때문이다.

3. Arrow function은 생성자로 사용할 수 없다.  일반 function은 isCallable한 특징, isConstructor한 특징을 모두 지니는 반면, Arrow function이 isCallable한 속성만 지니기 때문인데, isCallable한 특징과 isConstructor한 특징은 다음과 같이 정의할 수 있다.

   > [isCallable](https://tc39.github.io/ecma262/#sec-iscallable) : 함수 스코프에 정의된 처리들을 실행한다.
   > [isConstructor](https://tc39.github.io/ecma262/#sec-isconstructor): new 구문을 이용해 새로운 함수 객체를 생성한다.

   ES6에서는 isCallable과 isConstructor에 차이를 두는데, isConstructor한 함수는 new 키워드를 사용해야하고, isCallable한 함수는 함수식으로 호출할 수 있다. Arrow function은 호출만 가능하며, new 키워드를 통해 새로운 함수 객체로 생성될 수 없다. **객체로 생성될 필요가 없기 때문에 this를 바인딩 할 필요도 없게 되는 것이다.**

   ```js
   const func = {
     foo: () => {
    console.log("Arrow function's this === window:", this === window);
     },
     bar: function () {
    console.log("function's this === func ?", this === func);
     }
   }
   
   func.foo();
   func.bar();
   // Arrow function's this === window: true
   // function's this === func ? true
   ```
   
|                | isCallable | isConstructor |
| -------------- | ---------- | ------------- |
| function       | O          | O             |
| Arrow function | O          | X             |
| Class          | X          | O             |

