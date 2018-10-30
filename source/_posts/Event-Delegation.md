---
title: Event Delegation
categories: Dev
date: 2018-05-09 11:59:20
tag: Event
---


이벤트 위임을 한 문장으로 요약하면 `하위 요소에 이벤트를 붙이지 않고, 상위 요소에서 하위 요소의 이벤트들을 제어하는 방식`을 말합니다.


```html
<h1>오늘의 할 일</h1>
<ul class="itemList">
  <li>
    <input>
    <label>Item 1</label>
  </li>
  <li>
    <input>
    <label>Item 2</label>
  </li>
</ul>
```

```javascript
  var inputs = document.querySelectorAll('input');
  inputs.forEach(input => {
    input.addEventListener('click', event => {
      alert('clicked');
    });
  });
```

Javascript의 `querySelectorAll()`을 이용해 각 인풋 박스의 요소에 클릭 이벤트 리스너를 추가합니다. 화면을 실행시키고, 각 리스트 아이템의 체크박스를 클릭하면 경고 창이 표시됩니다. 


만약 리스트 아이템을 더 추가해야 한다면 어떻게 해야 할까요? 다음 코드를 추가하면 될까요?

```javascript
// 새 리스트 아이템을 추가하는 코드
var itemList = document.querySelector('.itemList');
var li = document.createElement('li');
var input = document.createElement('input');
var label = document.createElement('label');
var labelText = document.createTextNode('Item 3');

label.appendChild(labelText);
li.appendChild(input);
li.appendChild(label);
itemList.appendChild(li);
```

 위 코드를 추가해도 새로 추가된 리스트 아이템에는 클릭 이벤트 리스너가 동작하지 않습니다. 왜냐하면 새로 추가된 리스트 아이템에는 클릭 이벤트 리스너가 등록되지 않았기 때문입니다. 동적으로 요소가 추가되는 경우, 아직 추가되지 않은 요소는 DOM에 존재하지 않으므로 이벤트 핸들러를 바인딩할 수 없습니다. 

 리스트 아이템이 많아지면 많아질수록, 이벤트 리스너를 다는 작업은 번거로워집니다. 이 번거로움을 해결할 수 있는 방법이 바로 Event Delegation입니다.

```javascript
/*
var inputs = document.querySelectorAll('input');
inputs.forEach(function(input) {
	input.addEventListener('click', function() {
		alert('clicked');
	});
});
 */

var ul = document.querySelector('.itemList');
ul.addEventListener('click', function(event) {
	alert('clicked');
});
```
각 리스트 아이템마다 일일이 이벤트 리스너를 추가하는 대신 상위 요소인 UL태그에 이벤트 리스너를 등록하면, 하위에서 발생한 클릭 이벤트를 UL태그가 감지합니다.(Event Bubbling) 


Event Delegation를 사용할 때 얻을 수 있는 이점은 다음과 같습니다.

1. **동적 Element에 대한 이벤트 처리가 수월해진다.** => 상위 Element에서만 이벤트 리스너를 관리하기 때문
2. **Event Handler 관리가 쉬워진다.** => 동일한 Event를 한 곳에서 관리하기 때문
3. **메모리 사용량이 줄어든다.** => 동적으로 추가되는 Event가 없어지기 때문
4. **메모리 누수 가능성도 줄어든다.** => 등록 핸들러 자체가 줄어들기 때문