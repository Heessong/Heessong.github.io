---
title: 'HTTP'
date: 2021-04-22 16:11:02
category: 'HTML/CSS'
draft: false
---

> # HTTP 

<img src=https://media.vlpt.us/images/sunnu16/post/e27bb2cd-d4d6-465b-8ec3-be1a12ed070f/http%20communication.png>

`클라이언트`와 `서버`간의 정보교환을 가능하게하는 `통신규약`  

> ## Request  / Response 

### Request 

HTTP 요청은 `프론트(클라이언트)` 에서 `백(서버)`에 `데이터 처리` 를 시작하게 하기 위해 보내는 메세지다

- Start Line : 요청의 첫번째 줄에 해당.
  - HTTP method : 해당 요청이 의도하는것을 정의 `GET`, `POST`, `DELETE`
  - Request target : 해당 요청이 전송되는 목표 `url`
  - HTTP Version : HTTP의 버전 주로 1.1버전 사용
- Headers : 요청에대한 추가 정보를 담고있다
  - Host : 요청을 보내는 목표 `url`
  - User-Agent : 요청을 보내는 `클라이언트`의 정보 (ex. 브라우저)
  - Content-type : 요청이 보내는 메세지 `body`의 타입
  - Content-length : `body` 내용의 길이
  - Authorization : 회원의 `인증/인가` 처리를하기위해 `로그인 토큰`을 담는다
- Body : 요청의 실제 내용

### Response

- Start Line : 요청에 대한 상태를 `클라이언트`에게 알려주면서 시작한다

  - HTTP Version : 요청의 버전과 동일
  - Status Code : 응답 메세지의 상태코드
  - Status Text : 응답 메세지의 상태를 설명해주는 텍스트

- Headers : 요청과 동일

- Body : 요청과 동일

> ## Stateless

HTTP 통신은 독립적이기 때문에 과거의 통신내용을 알지못한다. 

그렇기때문에 매 통신마다 모든정보를 담아 계속 요청해야한다













