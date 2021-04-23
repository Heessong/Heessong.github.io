---
title: 'CSS 레이아웃'
date: 2021-04-14 14:11:02
category: 'HTML/CSS'
draft: false
---

> # Position

`position`은 CSS에서 요소의 위치를 정의하며 위치조정 속성에는

<ul>
  <li> static (기본값)
  <li> relative (상대위치)
  <li> absolute (절대위치)
  <li> fixed (고정위치)
</ul>

등이 있으며 `top`,`bottom`, `left`, `right` 좌표 속성을 사용하여 좀 더 상세하게 위치를 수정할수있다

### static (default)
아무런 위치를 지정하지 않는다 (기본값)
좌표 속성값를을사용할시 무시한다

### relative
static과 같은 기본위치이지만
좌표값이 적용가능해 상세위치수정이 가능하다

### absolute
부모요소를 기준으로 설정된 좌표 속성만큼 이동한다

### fixed
부모요소에 영향을 받지않으며 브라우저에 완전 고정되어 스크롤을 내려도 같은자리에 머물러있다.


> # inline, block, inline-block

`display` 속성의 값으로 사용되는것들로

### inline
`inline` 특성을 가지는 요소(inline 레벨)로 지정


### block
`block` 특성을 가지는 요소(block 레벨)로 지정
### inline-block
`inline-block` 특성을 가지는 요소(inline-block 레벨)로 지정
### none
해당 요소를 화면에 표시하지 않는다

> # float

`CSS`의 속성 구성하는데 필요한 `속성`

`float` 속성을 사용해 박스를 `왼쪽` 또는 `오른쪽`으로 정렬시키는 레이아웃 기법입니다.

`float`를 사용하면 문서의 흐름과 관계없이 화면 배치를 유연하게 할 수 있습니다.

float의 속성값으로는

<ul>
  <li>right (오른쪽으로 정렬)
  <li> left (왼쪽으로 정렬)
  <li>none (정렬하지 않는다)
</ul>
