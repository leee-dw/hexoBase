---
title: URI의 설계
categories: Dev
date: 2018-06-11 17:57:15
tag: 
- HTTP
- Web
- URI
---
{% callout info %}
#### {% fa info-circle %} 출처: <웹 개발자를 위한 웹을 지탱하는 기술>
{% endcallout %}


# URI의 설계

---

## 01. 쿨(Cool)한 URI는 변하지 않는다.

> Tim Berners Lee "URI는 변하지 않아야 한다. 변하지 않는 URI야말로 최고의 URI다" 주장.

---

## 02. 변하지 않는 URI를 만들기 위해서는

#### 프로그래밍 언어에 의존적인 확장자와 경로로 포함하지 않는다.

```
http://example.com/cgi-bin/login.pl
```

위 URI에는 구현에 의존적인 부분이 두 군데 있다. `'cgi-bin'`, `'.pl'` CGI 방식은 과거에 자주 사용되었지만, 성능면에서 문제점이 있었기 때문에 다른 방법으로 대체되었고, CGI 시대에 대부분의 웹 서비스는 Perl로 작성되었지만, 현재는 Ruby나, PHP 등으로 선택의 폭도 넓어졌다.



```
http://example.com/servlet/LoginServlet
```

확장자로 '.java' '.class'가 없는 건 좋아보이지만, 경로인 'servlet'은 특정 서블릿 컨테이너의 기본 경로이고 시스템을 서블릿에서 PHP로 바꾼 순간 변경된다. 또 'LoginSevlet'처럼 URI에 대문자를 사용하면, 다른 언어를 변경할 경우 그 URI은 사용할 수 없게 된다.



#### 메서드명과 세션ID를 포함하지 않는다.

```
http://example.com/Login.do?action=showPage
```

Struts 특유의 확장자인 '.do'도 문제지만, 더 큰 문제는 showPage라는 메서드명이 URI에 들어가 있다. 이것이 문제가 되는 이유는 같은 Struts 프레임워크를 사용하더라도, 시스템을 리팩토링하여 메서드명을 변경하면 바로 URI가 바뀌어 버리기 때문이다.



```
http://example.com/home.jsp?jsessionid=12345678
```

Java에서 세션ID를 Cookie가 아니라 URI에 집어넣으면 이런 'jsessionid'라는 파라미터를 포함한 URi를 생성한다. 하지만 세션ID는 로그인할 때마다 바뀌므로 이 URI는 시스템에 다시 로그인하면 변경된다.



#### URI는 리소스를 표현하는 명사로 한다.

URI는 명사라야 한다. HTTP에서는 리소스에 대해서 특정 HTTP 메서드만을 적용한다. 그리고 어떤 리소스를 취득할지 갱신할지는 URI로 지정하는 것이 아니라, URI에 적용하는 HTTP 메서드로 결정한다. 

즉, URI와 HTTP 메서드의 관계는 명사와 동사의 관계이다. 따라서 URI는 전체적으로 명사가 되도록 설계해야 한다.



#### URI 설계지침

1. URI에 프로그래밍 언어에 의존적인 확장자를 이용하지 않는다.(.pl, .rb, .do, .jsd 등)
2. URI에 구현에 의존적인 경로명을 이용하지 않는다(cgi-bin, servlet 등)
3. URI에 프로그래밍 언어의 메서드명을 이용하지 않는다.
4. URI에 세션ID를 포함하지 않는다.
5. URI는 해당 리소스를 표현하는 명사이다.



다음과 같은 URI가 Cool URI라고 할 수 있다. 

```
http://example.com/login
```

Cool URI란 심플한 URI이기도 하다.


---

## 03. URI 사용성

Cool URI의 또 다른 장점은 사용성(Usability)의 향상이다.

```
// 복잡한 URI
http://example.com/servlet/LoginServlet
```

```
// 심플한 URI
http://example.com/login
```

두 URI를 비교해보면

1. 글자 수 차이가 난다.
2. servlet은 일반인들에게 친숙하지 않은 단어다.



*기억하기 쉽고, 일반사람들도 사용하기 쉬운 것이 Cool URI의 장점이다.*

---

## 04. URI를 변경하고 싶을 때

URI를 변경해야 할 때는 가능한 한 Redirect하도록 해야 한다.

Redirect란 오래된 URI를 새로운 URI로 전송하는 HTTP의 기능을 말한다.

```
// 변경 전
http://example.com/old
```

```
// 변경 후
http://example.com/new
```

Redirect되어 있는 오래된 URI를 클라이언트가 취득하면 다음의 응답이 반환된다.

```
HTTP/1.1 301 Moved Permanently
Location: http://example.com/new
```



클라이언트는 301 Moved Permanently가 Redirect라는 것을 알고 있으므로, 자동적으로 Location 헤더에 명시된 새로운 URI로 이동한다. 

Redirect의 구현 방법은 HTTP 서버에서 준비한다. 만약 Apache라면, mod_rewrite 등의 모듈을 사용해 오래된 URI를 새 URI로 Redirect할 수 있다.

---

## 05. URI 설계의 테크닉

#### 확장자로 표현을 지정한다

* 콘텐트 네고시에이션
* 언어를 지정하는 확장자

#### 매트릭스 URI

URI는 슬래시(/)를 사용해 계층을 표현할 수 있다.

```
http://example.com/diary/2010/05/01
```



하지만, 모든 정보를 계층적으로 관리할 수 있는 것은 아니다. 지도 같이  다차원 정보를 가지는 것은 계층으로 표현할 수 없다.

매트릭스 URI는 계층구조를 표현하는 슬래시 대신 각각 파라미터를 세미콜론으로 구분해 리소스를 표현한다.

```
http://example.com/map/lat=35.605471;lng=139.642323
```

현재 매트릭스 URI를 표현할 때는 세미콜론이나 콤마가 사용되고 있다. 
세미콜론은 파라미터의 순서가 의미를 가지지 않는 경우, 콤마는 파라미터의 순서가 의미를 가지는 경우 사용된다.



예를 들어, 상기 URI에 있어서 'lat='과 'lng='를 생략하고, 파라미터 순으로 경도와 위도를 지정할 경우 다음과 같이 쓸 수 있다.

```
http://example.com/map/35.605471,139.642323
```


---

## 06. URI의 불투명성

웹에서의 리소스 조작은 HTML같은 리소스 내의 링크를 따라가며 이루어진다. 

즉, 클라이언트는 어디까지나 서버가 제공하는 URI를 그대로 사용할 뿐이다.

이렇게 클라이언트 쪽에서 구성하거나 확장자로 리소스 내용을 추단하거나 할 수 없는 특성을 **URI는 클라이언트에 있어 불투명하다** 라고 한다.

클라이언트를 만들 때는 URI가 불투명하다는 것을 염두에 두어야만 한다. 


---

## 07. URI를 강하게 인식하기

URI는 다음과 같은 점에서 아주 중요하다

* URI는 리소스의 이름이다.
* URI는 수명이 길다.
* URI는 브라우저가 어드레스 란에 표시한다.