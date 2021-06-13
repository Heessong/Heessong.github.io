---
title: '구글 검색결과에 블로그 노출시키기'
date: 2021-06-13 16:11:02
category: 'Etc'
draft: false
---

깃허브 블로그의 장점은 마크다운 에디터만으로 손쉽게 게시물들을 관리 할 수 있다는것이다. 

그리고 다른 블로그서비스들은 기본적으로 검색결과에 잘뜨지만 깃허브블로그는 따로 설정을 해주지않으면 구글이나 네이버의 검색결과에 보여지지 않아서 정말 나만의 일기장처럼 되어버린다. 

편안한 길 냅두고 멀리돌아가서 고생하는 나도 참 자기 복인거같긴한데 그래도 누가 시켜서가 아니라 순전히 나의 호기심때문에 고생하는건 밤새서해도 재밌는거같다 아무리 귀찮아도 깃허브 블로그로 해야지..😗 

그래서 깃허브 블로그를 네이버나 구글검색결과에 노출시키는방법을 찾아봤었는데  `구글 서치 콘솔`을 적용하면 검색결과에 뜨게 할 수 있었다. 

그때가 지금으로부터 3주전쯤이였나..? 

그때 대충대충 적용하고 자꾸 오류가나서 에이 안되나보다하고 말고 잊고있었는데 갑자기 메일 한통이 왔다

<br>

<img width="753" alt="스크린샷 2021-06-13 오후 3 22 52" src="https://user-images.githubusercontent.com/58321429/121797504-904d3000-cc5b-11eb-8a32-cafc55a9ebc9.png">

🤭.. 적용되고 있던거였니

<br>

![스크린샷 2021-06-13 오후 3 46 01](https://user-images.githubusercontent.com/58321429/121797966-7c56fd80-cc5e-11eb-8de7-f8038f05ee24.png)

구글검색에 뜨고있었구나.. 근데 그때 너무 대충 설정해놔서 그런지 전체게시글의 일부만 뜨고 있어서 이번기회에 처음부터 다시 설정을 했다! 

구글검색결과 반영에는 좀 시간이 걸리는거같긴한데 그래도 이번기회에 제대로 해놔야할거같아서 정리해보기!

<br>

### sitemap, robots 적용

전체적인 방향은 간단하다

내 블로그의 글들을 구글검색엔진의 크롤러가 크롤링 할 수 있게 해주는것!

즉! `sitemap.xml`과 `robots.txt`를 설정해주면 된다

`sitemap.xml`은 검색엔진에게 내 웹사이트의 위치와 목차 등 가이드의 역할을 한다고 보면되고` robots.txt`는 나의 웹사이트가 무엇을 얼만큼 크롤링 허용을 할지 설정해주는것이다!

그리고 내가 사용하고있는 `gatsby블로그` 테마의 개발자분(무려 한국인)이 이를 손쉽게 추가 할 수 있도록 틀을 잡아놓으셨다! 거기에 `React를 기반`으로 개발된 블로그라서 그나마 조금이라도 코드를 이해 할 수 있어서 정말 다행이였다

<br>

```
$ npm install gatsby-plugin-sitemap
```

원래라면 이렇게 sitemap.xml의 작성을 도와주는 라이브러리를 설치해주고 `gatsby-config.js` 파일에가서 설정을 해줘야했지만 

<br>

```javascript
module.exports = {
  ...
  plugins:[
    ...
    'gatsby-plugin-sitemap',
  ]
}
```

이미 설치되어 있었다! 👍

<br>

```javascript
module.exports = {
  ...
  siteUrl: `https://heessong.github.io`
 }
```

그리고 `gatsby-meta-config.js` 파일에가서 siteUrl에 본인 깃허브블로그 주소 넣어주기!

<br>

```javascript
{
      resolve: 'gatsby-plugin-robots-txt',
      options: {
        host: 'https://heessong.github.io',
        sitemap: 'https://heessong.github.io/sitemap.xml',
        policy: [
          {
            userAgent: '*',
            allow: '/',
          },
        ],
      },
    },
```

그리고 다시 `gatsby-config.js`파일로 돌아와서 `robots.txt`를 설정해준다!

`host`에는 본인의 깃허브 주소를 넣고

`sitemap`에 깃허브주소/sitemap.xml을 넣어주고

`policy`는 이전에말한 크롤링을 어디까지 허용해줄지 설정하는것인데 이에대한 명령어내용은 

https://developers.google.com/search/docs/advanced/robots/create-robots-txt?hl=ko 

구글검색센터에 정말 잘정리되어있다!

나는 뭐 딱히 크롤링제한 시킬건 없으니 전부다 공개로 설정!

<br>

### Google Search Console 적용

이제 구글 서치 콘솔을 적용해야하는데

https://improveyourank.com/%EA%B5%AC%EA%B8%80-%EC%84%9C%EC%B9%98%EC%BD%98%EC%86%94-%EC%84%A4%EC%B9%98%EB%B0%A9%EB%B2%95%EA%B3%BC-%EC%82%AC%EC%9A%A9%EB%B2%95/

이 블로그의 세번째 방법이 가장 간단하고 많이쓰여 나도 세번째방법으로 적용하였다

`meta tag를 잘복사해두자!`



```javascript
<Helmet
  ...
  meta={[
    ...
    {
      name: 'google-site-verification',
      content: 'xxxxxxbMePv2_xxxxx비밀코드_xxxxxxxxxx'
    }
  ]}
  ...
/>
```

그리고 이제 `src/head/index.jsx` 파일로가서 해당경로에 `content`에 복사해둔 `meta tag`를 이런식으로 넣어주면된다!

<br>

![스크린샷 2021-06-13 오후 4 40 36](https://user-images.githubusercontent.com/58321429/121799281-29814400-cc66-11eb-8a16-1e4bb634ea76.png)

그리고 마지막으로 다시 구글서치콘솔로 돌아가서 `Sitemaps탭`에서

`sitemap.xml`을 추가해주면 끝! 사람마다 반영되는게 다른데 나는 엄청 오래걸린거같다.. 추가해두고 까먹으면 되어있을거다!

<br>

![스크린샷 2021-06-13 오후 4 42 55](https://user-images.githubusercontent.com/58321429/121799325-6baa8580-cc66-11eb-94bf-d3c2384239ca.png)

며칠 기다리다가 URL를 검사해보면 URL이 등록되었다고뜨면 끝!

혹시 안되었다면 색인 생성 요청으로 해주면 된다! 요청하고 시간이 좀 걸리니 하루이틀 잊고 살자!

이제 내 블로그도 검색엔진에 뜨니 좀더 열심히 써야겠다

다음번엔 네이버 검색엔진에도 뜨게 할 예정! 😋😋😋