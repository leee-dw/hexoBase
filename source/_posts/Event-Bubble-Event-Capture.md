---
title: Event Bubble & Event Capture
categories: Dev
date: 2018-05-09 01:32:59
tag: Event
---

## 이벤트 버블링 Event Bubbling

이벤트 버블링이란, 특정 요소에서 이벤트가 발생했했을 때, 해당 이벤트 요소를 포함하고 있는 상위 부모 요소까지 이벤트가 전달되는 현상을 의미합니다. 

```html
<style>
  .number-one,
  .number-two,
  .number-three {
    width: 200px;
  }
  .number-one {

  }
  .number-two {
    background: #777;
  }
  .number-three {
    background: #ccc;
  }
</style>

<body>
  <div class="number-one">1
    <div class="number-two">2
      <div class="number-three">3
      </div>
    </div>
  </div>
</body>

<script type="text/javascript">
  var divs = document.querySelectorAll('div');
  divs.forEach(elem => {
    elem.addEventListener('click', event => {
      console.log(event.currentTarget.className);
    })
  })
</script>
```

위 코드는 세 개의 div 태그에 모두 클릭 이벤트를 등록하고, 버튼을 클릭했을 때  ` console.log(event.currentTarget);`를 호출하는 코드입니다.

![Event Bubbling](https://raw.githubusercontent.com/likedemian/Private-Studies/master/Personals/bubbling.png)

div 태그 하나만 클릭했는데, 3개의 이벤트가 발생하는 이유는 브라우저가 이벤트를 감지하는 방식 때문입니다. 브라우저는 특정 화면 요소에서 이벤트가 발생했을 때 그 이벤트를 최상위에 있는 화면 요소까지 전달합니다(Event Bubbling). 

따라서, 클래스명 `number-three` => `number-two` => `number-one` 순서로 div 태그에 등록된 이벤트들이 실행됩니다. 만약, 두 번째 태그를 클릭했다면 `number-two`=>`number-one` 순으로 클릭 이벤트가 동작합니다. 이처럼 자식 이벤트 요소에서 부모 이벤트 요소로 이벤트를 전파하는 방식을 **이벤트 버블링(Event Bubbling)**이라고 합니다.

---

## 이벤트 캡쳐링 Event Capturing

자식 요소에서 특정 이벤트가 발생했을 때 최상위 요소인 body 태그에서 자식요소 태그를 찾아 내려가는 특성을 **이벤트 캡쳐링**이라고 합니다.
이벤트 캡쳐링 구현하는 방법은 다음과 같습니다.

```html
<style>
  .number-one,
  .number-two,
  .number-three {
    width: 200px;
  }
  .number-one {
    background: #000;
  }
  .number-two {
    background: #777;
  }
  .number-three {
    background: #ccc;
  }
</style>

<body>
  <div class="number-one">1
    <div class="number-two">2
      <div class="number-three">3
      </div>
    </div>
  </div>
</body>

<script type="text/javascript">
  var divs = document.querySelectorAll('div');
  divs.forEach(elem => {
    elem.addEventListener('click', event => {
      console.log(event.currentTarget.className);
    }, {
      capture: true; // default는 false.
    })
  })
</script>
```

`addEventListener()` 옵션 객체에 `capture:true`를 설정해주면 캡쳐링 됩니다. 그리고 이벤트 버블링과 반대 방향으로 탐색을 시작합니다.
`<div class="number-three">3 </div>`를 클릭하면 다음과 같은 결과가 나타납니다.

![Capturing](https://raw.githubusercontent.com/likedemian/Private-Studies/master/Personals/capturing.png)




주의할 것은 버블링과 캡처링은 둘 중에 하나만 발생하는 것이 아니라 캡처링부터 시작하여 버블링으로 종료합니다.
즉, 이벤트가 발생했을 때 캡처링과 버블링은 순차적으로 발생한다.