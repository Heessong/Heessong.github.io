---
title : 'Nav바가 상단에 걸릴때 변하게 만들기!!'
date : 2021-05-22 21:03:10
category : 'React.js'
draft : true
---

<img src=https://user-images.githubusercontent.com/58321429/119220274-b2ec9d00-bb24-11eb-9755-87b5c73759b0.gif>

프로젝트를 진행하던 중

### FilterBar ( 부모컴포넌트 )

```javascript
filterBar = React.createRef();  //Ref

<div className="filterBar" ref={this.filerBar}>
    .....
    .....
</div>
```

Ref  -> DOM엘리먼트에 직접 접근하여 수정



```javascript
componentDidMount() {
    window.addEventListener('wheel', this.handle);
  //마우스 휠 이벤트 발생시 handle() 실행
```

휠 이벤트 Mount



```javascript
handle = () => {
    this.filterBar.current.getBoundingClientRect().top <= 0 
  //filterBar ref가 부착된 엘리먼트의 화면상단으로부터의 높이값 < 0
      ? this.setState({ offsetTop: true })
      : this.setState({ offsetTop: false });
  };
```

![스크린샷 2021-05-21 오후 1.07.29](/Users/hwisung/Desktop/스크린샷 2021-05-21 오후 1.07.29.png)ref



```javascript
<FilterBarExtend styleChange={this.state.offsetTop} />
```



### FilterBarExtend ( 자식 컴포넌트 )

