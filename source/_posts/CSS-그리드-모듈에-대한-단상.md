---
title: CSS 그리드 모듈에 대한 단상
categories: Dev
date: 2018-05-10 19:29:57
tag: 
- CSS
- grid
---
## Float grid modules VS. Grid layout systems

Float 속성을 활용해 Grid를 제작할 때 겪는 불편은 Float 엘리먼트가 가지는 특성에서 비롯된다. Float 엘리먼트의 특정은 기본적으로 부모 엘리먼트의 높이에 영향을 주지 않는데, Grid Module을 제작하기 위해서는 Float된 자식 엘리먼트의 높이가 부모 엘리먼트에 반영되도록 설정해야 하기 때문이다. 

Float 자식 요소의 높이가 부모 요소에 반영되도록 하기 위해 가상 선택자 `:after`에 `clear` 속성을 부여한다. `clear` 속성은 취소한다는 뜻이며,  Float Grid Module을 위해 일반적으로 사용하는  `clear: both` 속성은 좌우공간을 삭제한다. 

가상 선택자를 생성한 뒤 `display: block; clear: both`  속성을 추가하면, 의미없는 빈 엘리먼트를 사용하지 않으면서도 Float은 clear된다. 이 방법은 clearfix hack라고 불리는데, 사용법은 아래와 같다.

```css
.div:after {
    content: ""; 
    display: block; 
    clear: both;
}
```

![float-clear](https://user-images.githubusercontent.com/23162772/39863422-912def28-5481-11e8-8d0a-a6ec8b0cbbd6.png)

처음 Float를 사용할 때는 Float가 지닌 기본 속성*(Float 요소는 부모 요소의 높이값에 영향을 주지 않는 다는 점)*을 파악하기 어려웠고, clearfix hack같은 속성을 추가해야 하는 이유도 알지 못했다. 그래서 Float Grid module 제작은 개발 초보들을 향한 일종의 장벽이라고 생각했다.

반면, CSS Grid layout system은 먼저 X축과 Y축 격자를 모두 설정하고, 격자 내에 요소를 배치한다. 또한 float grid처럼 clearfix hack을 별도로 설정할 필요가 없으며, grid와 flexbox를 혼용해서 사용할 수 있다(전체 레이아웃을 Grid로 짠 뒤, 세부 목록을 Flex로 제작하는 방식 등). 때문에 grid layout system은 높은 자유도와 효용성을 지닌 속성이라고 생각했다.



## CSS Grid layout system을 사용하면서 알게 된 팁

1. CSS Grid layout을 사용하면 행을 감싸는 별도의 div wrapper로 감싸지 않고도 2차원 레이아웃을 구현할 수 있다는 것을 알았다(`float`을 쓰면 각 행을 구성하는 엘리먼트를 별도의 마크업으로 감싼 뒤 `float` 속성을 주고, 또 그 다음 행에 미치는 영향을 없애기 위해 그것을 ‘clear’해 주어야 한다).

2. Grid layout에서 사용가능한 `fr` 단위는 Grid container 내 잉여 공간의 일정 비율을 나타낸다. 잉여 공간의 크기에 따라 자유롭게 너비를 확장 또는 축소할 수 있다.

3. 아이템들을 그리드 영역 위에 겹쳐 쌓을 수 있다. 아이템은 `z-index`를 준수하기 때문에, 여러 아이템을 동일한 그리드 셀 위에 포개어 다양한 스코프를 만들 수 도 있다.

4. 2018년 5월 10일 기준, 약 87%의 브라우저들이 Grid layout을 지원한다. (Source: Can I Use)

  ![CSS-Grid-Browser](https://user-images.githubusercontent.com/23162772/39863427-984df3e8-5481-11e8-891f-1b08923f6fd9.png)



## CSS Grid layout system을 사용하면서 아쉬운 점

없습니다.