---
title: id & class
categories: Dev
date: 2018-04-19 12:30:52
tag: 
- HTML
- CSS
- Mark up
---

## id 속성

```html
<style>
  #pullquote {
    color: #7fadee;
    font-weight: 700;
  }
</style>
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Suscipit necessitatibus nam provident, enim debitis harum dignissimos
    repellat sequi recusandae a omnis, cum quae similique. Delectus quod reprehenderit ut qui commodi.</p>
  <p id="pullquote">Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum eaque, harum, repudiandae error eos, rerum illum obcaecati
    distinctio nisi eveniet ab tempora sequi delectus? Labore ipsa debitis quo ex tempore!</p>
  <p>Lorem ipsum dolor sit, amet consectetur adipisicing elit. Voluptatibus recusandae deleniti nesciunt necessitatibus natus
    facilis fugiat vero iste quas fuga, consectetur delectus suscipit libero blanditiis! Sapiente consequatur maiores incidunt
    quibusdam!
  </p>

```

![id](https://raw.githubusercontent.com/likedemian/Private-Studies/master/Personals/id.png)

- 페이지에 있는 다른 요소들과 해당 요소를 고유하게 식별하는 데 id속성을 사용한다.
- id 속성의 값은 **알파벳 또는 밑줄로만 시작해야 하며 숫자나 다른 문자로 시작하면 안 된다.**
- 특히 동일한 페이지에 있는 **요소의 id 속성 값은 같으면 절대 안된다**.
- 요소에 고유한 id를 부여하여 페이지에 있는 동일한 요소에 다른 스타일을 적용할 수 있다.
- 예컨대 페이지에 있는 한 단락에만 색다르게 스타일을 적용할 수 있다.
- id 속성은 모든 요소에서 사용할 수 있으므로 전역 속성이라고도 한다.

---

## class 속성

```html
<style>
  .important {font-weight: 700;}
  .admittance {color: #f0f;}
</style>

<p class="important">Lorem ipsum dolor sit amet consectetur adipisicing elit. Suscipit necessitatibus nam provident, enim debitis harum dignissimos
    repellat sequi recusandae a omnis, cum quae similique. Delectus quod reprehenderit ut qui commodi.</p>
  <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum eaque, harum, repudiandae error eos, rerum illum obcaecati
    distinctio nisi eveniet ab tempora sequi delectus? Labore ipsa debitis quo ex tempore!</p>
  <p class="important admittance">Lorem ipsum dolor sit, amet consectetur adipisicing elit. Voluptatibus recusandae deleniti nesciunt necessitatibus natus
    facilis fugiat vero iste quas fuga, consectetur delectus suscipit libero blanditiis! Sapiente consequatur maiores incidunt
    quibusdam!
```

![class](https://raw.githubusercontent.com/likedemian/Private-Studies/master/Personals/class.png)



- 모든 HTML요소에 class 속성을 추가할 수 있다.
- 문서 내에서 고유하게 하나의 요소를 식별하기보다는 **페이지에서 몇 개의 특정 요소들을 식별하려는 경우**에 사용한다.
- 중요한 정보가 포함된 일부 텍스트 단락이 있어 이러한 요소를 구분하거나, 현재 사이트 내의 페이지를 가리키는 링크와 외부 사이트를 가리키는 링크를 구분하는 경우 class 속성을 사용하여 수행할 수 있다.
- **요소에 있는 class 속성은 동일한 값을 공유한다.**