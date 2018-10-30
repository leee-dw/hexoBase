---
title: AJAX - Ajax 요청방법
categories: Dev
date: 2018-06-09 12:17:23
tag: AJAX
---

---

`XMLHttpRequest`: 객체를 생성한다.

---

`.open('string method', 'string url', [boolean async, string user, string password])`: HTTP 메서드와 주소를 설정하고, 요청을 준비한다.
  - `'string method'`: HTTP 요청방식이다. 
    - 확실하게 구현된 요청방식들은 'GET' , 'POST', 'HEAD'가 있다.
    - 구현체들은 'CONNECT', 'DELETE', 'OPTIONS', 'PUT', 'TRACE', 'TRACK' 요청 방식들도 지원하게 될 것이다.
  - `'string url'`: 요청을 처리할 페이지의 URL
    - URL은 현재 스크립트가 포함된 문서의 URL을 기준으로 한다.
    - URL은 요청을 생성하는 스크립트를 포함한 문서와 동일한 호스트명과 포트를 사용해야 한다.
    - XHR2에서는 CORS를 지원하는 서버로 교차 출처 요청을 보내는 것이 허용된다.
  - `[boolean async, string user, string password]`: 
    - `boolean async`: 전달인자가 async를 지정하였고, 값이 false면, 요청은 동기방식으로 수행된다.
    - `string user`, ``string password`: HTTP 요청과 함께 사용할 시용자명과 비밀번호를 지정한다.
  - XMLHttpRequest 객체를 재설정하며 전달인자는 이후 `send()` 메서드에서 사용하기 위해 저장해둔다.
 
---

`.send()`: open() 메서드 후 준비된 요청을 전달하는 메서드이다.
  - HTTP 요청 방식과 URL, 인증서는 이전에 open() 메서드 호출 시 지정했다.
  - 이전의 setRequestHeader()를 호출함으로써 지정된 요청헤더.
  - 이 메서드에 전달인자 body를 넘긴다. body는 문자열이거나 요청 본문을 지정하는 문서 객체 또는 요청 본문이 따로 존재하지 않는 경우 생략하거나 null일 수 있다. XHR2에서는 요청 본문으로 ArrayBuffer나 Blob, FormData 객체를 사용할 수도 있다.
  - 괄호 내에 서버에 전달될 추가 정보를 저장 가능하며, 추가 정보가 전달되지 않으면 null 키워드를 사용한다.
  - ex) xhr.send(null)

---