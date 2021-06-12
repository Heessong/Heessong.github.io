---
title : '로그인 인증, JWT Token'
date : 2021-05-09 18:59:22
category : 'Javascript'
draft : false
---

백엔드와의 첫 연결테스트로 회원가입 및 로그인인증을 진행하였다

네트워크 연결에 어려움이 있었지만 어찌어찌 해결을하고 실습을 진행하였는데 신기했다!

<br>

```javascript
fetch('http://10.58.3.66:8000/user/login', {
      method: 'POST',
      body: JSON.stringify({
        email: this.state.inputId,
        password: this.state.inputPw,
        name: '김휘성',
        nickname: 'we휘성',
        phone_number: '01015411541',
        age: 25,
      }),
    })
```

첫번째로 프론트에서 입력받은 데이터를 `JSON`에서 `string`값으로 변환하여 백엔드의 회원가입 엔드포인트로 데이터를 전송한다.

 `fetch API`에서의 `method`값으로 `GET`은 데이터를 수신하는것이고 `POST`는 데이터를 송신하는것이다. 

우리는 현재 백엔드에게 데이터를 전송해야하니 `POST`로 설정하였다. 클라이언트에 이메일과 비밀번호 입력칸 2개뿐이 없었던터라 올바른 전송을위해 임시로 데이터값을 하드코딩으로 넣어주어 테스트를 진행하였다. 

백엔드와 프론트엔드 서로의 `key`값이 동일하지않으면 오류가 발생하기 때문이다.

<br>

```javascript
.then(response => response.json())
      .then(result => {
        if (result.MESSAGE === 'SUCCESS') {
          localStorage.setItem('token', result.token);
          this.props.history.push('/main-hwisung');
        } else {
          alert('아이디나 비밀번호를 확인해주세요!!');
        }
      });
```

이렇게 백엔드에게 데이터를 전송해주면 백엔드에서 `key`값이 일치하는지 확인후 데이터를 저장하고 프론트엔드는 다시 응답받은 데이터를 `JSON`파일로 변환하여 읽는다.

`result`는 백엔드로부터 받은 응답에대한 데이터를 담고있는 객체이다.

백엔드에서의 회원가입, 로그인이 성공하여 `result`라는 객체안의 메세지가 `SUCCESS`라는 내용을 담고있으면 백엔드로부터 받은 `token`을 `localStorage`에 저장후 메인페이지로 이동한다

만약 아이디나 비밀번호가 불일치하여 백엔드로부터 `SUCCESS` 메세지를 받지못하면 `alert`창이 뜨게된다.

어찌보면 간단한 백엔드와 프론트엔드의 첫연결이였지만 신기하고 재밌었고

앞으로의 프로젝트가 겁나기도하지만 기대도된다