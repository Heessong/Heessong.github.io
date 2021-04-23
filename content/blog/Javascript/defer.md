---
title: 'async와 defer'
date: 2021-04-21 23:11:15
category: 'Javascript'
draft: false
---

웹브라우저는 `script` 파일을 다운로드-해석-실행이 완료 될 때까지 `HTML parsing`작업의 우선순위를 뒤로 미룬다. 

그래서 용량이 큰 `script` 파일이 있을경우에는 실행이 완료되기까지 비교적 오래 걸리기 때문에 전체적인 페이지 로딩속도가 느려질수가 있다.

이러한 현상을 개선하기위해 나온것들이 `async`와 `defer`속성이다 

> # async 

<img src=https://blog.asamaru.net/res/img/post/2017/05/script-async-defer-2.png>

`HTML parsing`과 병행하여 `script`를 불러온후 `script`가 준비될때마다 실행된다.

그러므로 실행의 순서가 중요한 `script`의 경우에는 `async`사용시 유의해야한다. 



> # defer

<img src=https://blog.asamaru.net/res/img/post/2017/05/script-async-defer-3.png>

`HTML parsing`이 실행되는동안 `script` 파일을 불러오며 `parsing`이 끝나면 그때 `script`를 실행한다. `script`가 먼저 다운이 완료되어도 `HTML parsing`이 끝나기전까지는 실행되지않는다.

`async`와는 다르게 호출된 순서대로 실행된다.

<strong>script가 문서를 직접 만지고 조작하거나 서로 간 로딩 순서가 중요할 때에는 defer 속성을 쓰고, 그렇지 않다면 async 속성을 써서 웹 페이지 로딩 속도를 줄일 수 있다 .</strong>
