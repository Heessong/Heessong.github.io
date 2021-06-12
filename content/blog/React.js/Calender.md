---
title : 'react-dates로 달력 만들기'
date : 2021-05-30 21:03:10
category : 'React.js'
draft : true
---
드디어 2차 프로젝트가 시작되었다.  
우리팀의 목표는 에어비앤비를 클론코딩하는것!  
어떻게 생겼나 들어가보니..  
메인화면에 떡하니 있는 캘린더..
![에어비앤비](https://user-images.githubusercontent.com/58321429/120111209-05c0f700-c1ac-11eb-8fb6-4eaef20961d8.gif)

<br>

대체 이걸 어떻게 만들지...? 뒤에계시던 종택멘토님의 말씀..  
**직접 만들면 달력 만드는거만 2주가 걸릴 수 있어요**  
😱😱😱그럼 어떻게해야하나요..  
그 답은!  
바로 에어비앤비에서 제공하는 `react-dates` 라이브러리다!
<img src=https://raw.githubusercontent.com/airbnb/react-dates/master/react-dates-demo.gif>
처음엔 그냥 api문서 보고 필요한거 가져다가 붙이면 되겠거니 생각했다

<br>

![api](https://user-images.githubusercontent.com/58321429/120111740-1b372080-c1ae-11eb-82df-57af01852889.gif)

아


<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

뭐 정확하게는 몰라도 어찌어찌 읽었다..     
`react-dates` 달력의 기본디자인을 에어비앤비의 달력과 똑같이 만들어야하므로 `css` 스타일속성을 변경하는법을 문서에서 찾았는데
라이브러리 문서에서 알려주는건 4개인가 5개의 속성밖에 없었다...  
이거로 다 바꿀수있는줄 알았는데 아무리 변경해봐도 안되는것이였다..  
그래서 라이브러리가 설치된 `node_modules` 폴더에 들어가서 달력에 적용된 `css` 파일을 열어보았다.  
거기서 `css`속성을 변경해주면 쉽게 변경할수있겠지?  

![달력](https://user-images.githubusercontent.com/58321429/120112206-dad8a200-c1af-11eb-8e95-e23d50bcff0b.gif)

아

<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>
<br>

![비어비앤비달력](https://user-images.githubusercontent.com/58321429/120112420-bc26db00-c1b0-11eb-9909-8a8c20499a3e.gif)
>임시구현.. 갈길이 멀다 

달력 라이브러리의 종류  
react-dates를 선택한 이유  
DateRangePicker,DateRangeController의 차이   
Controller를 적용했을때 처음에 작동안하는이유   
클래스형 reactdates - 함수형으로 전환 , 훅스  
체크인 체크아웃 날짜 - 프롭스  
moment.js 다루기  
