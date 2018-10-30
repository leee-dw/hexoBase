---
title: Sass를 활용한 반응형 스타일 제작
categories: Dev
date: 2018-06-06 18:33:32
tag: Sass
---
## Introduction

코드스쿼드 레벨3 코스 중 두 번째 과정인 웹페이지 화면을 구현하는 과제를 시작했다. 그 중 Sass를 사용하면서 겪은 문제들과 느낀 점을 기록한다. 

컴포넌트를 재사용하거나, 반응형 페이지를 제작하는 경우 반복적으로 들어가야 할 코드들이 많은데, 일일이 CSS에 속성값을 부여하는 일은 번거롭게 느껴졌고, Sass, PostCSS 등 많은 CSS pre-processor들이 등장하는 상황에서 굳이 CSS를 고집할 이유가 없다고 생각했다. 

뿐만 아니라, Sass를 사용하면 CSS에 변수와 반복문 조건문 등을 사용해 코드를 작성할 수 있기 때문에, 함수를 작성하는 것처럼 CSS를 사용할 수 있어 더 편리했다.



## SCSS vs. Sass

나는 SCSS 대신 Sass를 사용하기로 했다. SCSS는 CSS와 유사하고, 더 알아보기 쉽다고 하지만, 상대적으로 Sass를 작성할 때 느끼는 편리함이 내겐 더 큰 이점으로 다가왔다.
Sass가 편리하다고 생각한 이유는  `{`, `}`, `;` 없이 들여쓰기(indentation)만으로 속성값을 부여할 수 있어, 괄호와 세미콜론를 작성하는 수고를 덜 수 있기 때문이고,  =, + 기호같은 단축표기법으로 `@mixin `과 `@inclue` 명령어를 사용할 수 있기 때문에 훨씬 간단하다고 생각한다. 

다만, 일부 개발자들은 Sass 문법에 익숙하지 않아 현재 Sass의 주문법은 SCSS라고 하는데, 나로서는 안타까운 일이다.



## Sass 폴더구성

일단 HTML 마크업을 BEM 형태로 제작했다. BEM을 사용해서 제작하면 HTML의 Class name이 길어져서 가독성이 떨어지는 문제가 발생하지만, Block별로 클래스 네이밍을 부여하기 때문에 Block별로 Sass 파일을 나누어 제작할 수도 있을 것 같았다.

Block 별로 나누어 관리하게 되면 CSS의 어느 속성을 변경했을 때, 어느 블록에 있는 어떤 속성값이 변했는지 파악하기 쉽고, 유지보수에도 유리할 것이라고 판단했다.

아직은 제작 초기지만, 아래와 같이 블록을 나누어 Sass 파일을 제작했다.

```bash
├── app.sass
├── base
│   ├── _reset.sass
│   └── _typography.sass
├── footer
│   └── _footer.sass
├── header
│   ├── _categories.sass
│   ├── _left-nav.sass
│   ├── _main-nav.sass
│   └── _right-nav.sass
├── main
│   ├── content
│   │   └── _main-content.sass
│   ├── loader
│   └── slider
│       └── _main-slider.sass
└── utils
    ├── _mixin.sass
    └── _variables.sass
```

app.sass 파일은 모든 Sass 파일들을 관리해서, CSS로 변환하는 기능을 한다.

그 아래 base 폴더에 위치한 _reset.sass와 _typography.sass에는 페이지 제작을 위해 필요한 속성을 초기설정하는 역할을  부여했다. _reset.sass 파일은 [Eric Meyer의 Reset Tool](https://meyerweb.com/eric/tools/css/reset/)을 변형했고,  _typography.sass 파일에는 [Google Font](https://fonts.google.com/)와 [Material Icon]()의 웹폰트들을 @import 했다.

페이지 내 영역별로 나누어 관리하고자 header / main / footer 폴더로 나누었고, 나누어진 각 폴더 안에는 또 다시 블럭 별로 나누어 파일을 제작했다. util 폴더에는 _mixin.sass 파일과 _variables.sass 파일을 넣었다. 각 파일에는 반응형 웹 제작에 필요한 해상도별 상태값과 속성을 부여했고, 해상도가 변경될 때마다 _variables.sass에 있는 변수들을 속성값으로 부여할 수 있도록 지정했다.





## Sass를 활용한 반응형 제작

먼저 Sass를 활용해서 반응형에 적합한 CSS 코드를 제작했다. 

```scss
/* ******************************************************** */
/*                      Screen size                         */
/* ******************************************************** */  
$desktop-large-size: "(min-width: 1920px)"
$desktop-medium-size: "(min-width: 1024px) and(max-width: 1919px)"
$desktop-small-size: "(min-width: 768px) and (max-width: 1023px)"
$tablet-size: "(min-width: 425px) and (max-width: 767px)"
$mobile-size: "(max-width: 424px)" 
```

위 코드에서 보다시피 먼저 스크린 사이즈를 `$desktop-large-size`, `$desktop-medium-size`, `$desktop-small-size`, `$tablet-size`, `$mobile-size` 와 같이 5개의 변수로 지정한 뒤 각 변수들을 아래 코드처럼 배열로 묶어 사용했다.



```scss
$screen-size-array: ($desktop-large-size, $desktop-medium-size, $desktop-small-size, $tablet-size, $mobile-size)
$screen-size-count: length($screen-size-array)
```

 5개의 변수 `$desktop-large-size`, `$desktop-medium-size`, `$desktop-small-size`, `$tablet-size`, `$mobile-size` 에 괄호를 사용해 묶으면 배열로 사용할 수 있고, length() 메서드로 사용하면 배열의 길이를 알 수 있다. 

Sass Documentation을 찾아보며 여러 기능들을 익혀 사용했지만. 배열처럼 사용하는 건 Sass Documentation에서도 찾지 못해 그런 기능이 있는 줄도 몰랐다. 그래도 혹시나 하는 마음에 구글링을 해보니, 외국 개발자가 포스팅한 블로그에서 발견해 사용했다.



```scss
=screen-width($size)
  @each $device, $screen, $width in (desktop-large-size, $desktop-large-size, $desktop-large-width), (desktop-medium-size, $desktop-medium-size, $desktop-medium-width), (desktop-small-size,$desktop-small-size, $desktop-small-width), (tablet-size, $tablet-size, $tablet-width), (mobile-size, $mobile-size, $mobile-width)
    @if "$size == #{$device}"
      @media screen and #{$screen}
        width: $width		
```

그리고 아래 코드와 같이 반복문을 활용해 스크린 사이즈에 맞는 width값을 지정했다.

```scss
.main__cinemas__list__body__slider__contents__item
  @for $i from 0 to $screen-size-count 
    +screen-width(#{$i})
```

Sass를 단순히 indention을 넣지 않을 요량으로만 사용했는데, 반복문과 조건문, 변수지정은 물론 배열로도 묶을 수 있어서 놀랐다. 일반적으로 반응형 제작을 노가다에 빗대는 경우가 종종 있는데, Sass를 사용하면 노가다하지 않고도 제작할 수 있겠다.