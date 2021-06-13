---
title: '위솝 프로젝트 끝!!'
date: 2021-05-23 02:11:02
category: 'Etc'
draft: false
---
위코드에 온지 1달만에 1차 프로젝트가 시작되었고 12일간의 1차 프로젝트가 드디어 끝났다. 개강한게 엊그제같은데 시간 정말 정말 빠르다...🙄

프로젝트 시작전에는 프로젝트를 하는것에대한 기대와 설렘이 있었고 빨리하고 싶은마음도 굴뚝같았었다!!

<img src=https://media.giphy.com/media/l0HluguW85hC2FFmM/giphy.gif width=300> 

그리고 1차 프로젝트가 정말 시작되었고..!!
프로젝트를 진행하면서도 정말 어렵고 피곤하기도했었지만 진심으로 재밌었고 흥미진진한 경험이였다 🙄

우리팀은 스킨케어 브랜드 이솝을 벤치마킹하여 기획과 디자인에 소요되는 시간을 최소화하며 프로그래밍에 중점을두고 시간을 투자하고자 클론코딩을 진행하였다

그중에 내가 맡은부분은 상품리스트, 상품의 상세페이지, 장바구니 추가를 담당했다



### 상품리스트
<img src=https://user-images.githubusercontent.com/58321429/119232717-32985d00-bb61-11eb-8d5f-f6ef460ca002.gif>
말그대로 상품의 목록들을 보여주는 부분이였는데 백엔드의 데이터를 fetch해와서 출력해주면 되는부분이다.
마우스 포인팅시 사이즈가 1개인 상품은 가격과 용량이 고정이지만
사이즈가 여러개인 상품은 사이즈 선택 버튼이 생기며 버튼을 클릭하면 가격이 변경된다.



### 상세페이지
<img src=https://user-images.githubusercontent.com/58321429/119232825-860aab00-bb61-11eb-97a8-d502ab768b9d.gif>
상품리스트에서 한가지 상품을 클릭하면 해당 상품의 상세정보를 볼 수 있는 페이지로 넘어간다.
상품에대해 더욱 상세한 정보를 볼 수 있고 마찬가지로 사이즈 선택을 할 수 있고
선택시 가격과 사진이 변경된다. 사진에 보이는 사진은 단순히 확대한것이 아닌 정확히 2배 용량이다😏



### 장바구니 추가
<img src=https://user-images.githubusercontent.com/58321429/119232834-8dca4f80-bb61-11eb-9d4f-6ee36cab1f0c.gif>
카트에 추가 버튼을 누르면 해당 상품의 id값과 size값이 백엔드 서버로 전송되어 백엔드에서 이 2가지 정보와 일치하는지 확인후 일치한다면 장바구니 컴포넌트로 해당상품의 정보를 전송하며
장바구니에 해당 상품이 담기게된다.  



### 필터바
<img src=https://user-images.githubusercontent.com/58321429/119220274-b2ec9d00-bb24-11eb-9755-87b5c73759b0.gif>
정말 어려웠던 컴포넌트.. 아직도 많이 헷갈린다.. 처음에 렌더링 후 스크롤바를 내리다가 상단바에 걸리면 필터바의 디자인이 바뀌며 고정된다. 
애니메이션 부분은 팀원이자 스승님이신 도은님의 도움으로 성공적으로 구현했지만 필터링 기능부분은 아직 시간이 부족해 미완성이라 많이 아쉽다.. (애니메이션은 따로 블로깅 예정)
나중에 시간이 난다면 반드시 완성 시키고 말겠다



``` javascript
//필터바 부모컴포넌트
componentDidMount() {
    window.addEventListener('wheel', this.handle);

    fetch(
      PRODUCTS_BASE_URL
        ? `${PRODUCTS_BASE_URL}/products?category_id=1`
        : `/data/category_id=1.json`
    )
      .then(categorys => categorys.json())
      .then(categorys => {
        const categories = {};
        categorys.result.forEach(category => {
          categories[category[0].category_id] = categories[
            category[0].category_id
          ] || {
            menu_id: category[0].menu_id,
            menu_name: category[0].menu_name,
            category_id: category[0].category_id,
            category_name: category[0].category_name,
            feature_category_name:
              category[0].product_features[0].feature_category_name,
            features: category[0].product_features[0].features,
            features_use: category[0].product_features[1].features,
            product_ingredients: category[0].product_ingredients,
          };
        });
        this.setState({
          category: Object.values(categories),
        });
      });
  }
```
<img src=https://media.giphy.com/media/ztCmrnCN7jvby/giphy.gif width=250>

0 하나 . 하나만 틀려도 렌더링시 버그가 빗발치는 공포의 중복데이터 걸러내기 과정 🧐
진짜 눈 크게 뜨고 엄청 세세하게 봤고 결국엔 해냈다....! 

``` javascript
//필터바 자식 컴포넌트
  componentDidMount() {
    const skinType = {};
    const themeUse = {};
    const themeSmell = {};
    let skinTypeCategory = [];
    let themeUseCategory = [];
    let themeSmellCategory = [];

    this.state.category.forEach(category => {
      skinType[category.features] = skinType[category.features] || {
        check_features: category.features,
      };
    });
    Object.values(skinType).forEach(ele => {
      ele.check_features.forEach(type => {
        if (!skinTypeCategory.includes(type)) {
          skinTypeCategory.push(type);
        }
      });
    });

    this.state.category.forEach(category => {
      themeUse[category.features_use] = themeUse[category.features_use] || {
        check_features_use: category.features_use,
      };
    });
    Object.values(themeUse).forEach(ele => {
      ele.check_features_use.forEach(type => {
        if (!themeUseCategory.includes(type)) {
          themeUseCategory.push(type);
        }
      });
    });

    this.state.category.forEach(category => {
      themeSmell[category.features_use] = themeSmell[category.features_use] || {
        check_product_ingredients: category.product_ingredients,
      };
    });
    Object.values(themeSmell).forEach(ele => {
      ele.check_product_ingredients.forEach(type => {
        if (!themeSmellCategory.includes(type)) {
          themeSmellCategory.push(type);
        }
      });
    });

    this.setState({
      skinType: skinTypeCategory,
      themeUse: themeUseCategory,
      themeSmell: themeSmellCategory,
    });
  }
```
그리고 이 필터바에서는 백엔드의 상품데이터 전체를 fetch해와서 중복되는 요소들을 제거하여 카테고리 리스트에 출력해주고 다시 데이터를 재가공해서 체크박스 리스트로 출력해주는 방식으로 진행하였는데
멘토님께서 이러한 방식은 할 수는 있지만 굉장히 비효율적인 방식이라 어지간하면 하지말라고 하셨다.
많은시간을 투자했지만 옳지않은방법이였다니 조금 아쉬웠지만 그래도 데이터 구조분해에 대한 지식은 많이 얻어서 나쁘지 않다고 생각한다. 
그렇게 생각해야 마음이 놓인다 🤥.
지금봐도 불필요한 코드가 굉장히 많이있는거같아서 추후에 리팩토링을 필수로 진행 할 예정이다.. 



### 느낀점

<img src=https://media.giphy.com/media/148k3l7yAK0LN6/giphy.gif>
<img src=https://media.giphy.com/media/dEdgB3euossMg/giphy.gif width=250 height=156>

너무 밤늦게까지 하지 말자!! 구현속도가 느린거같아서 새벽까지 무리 좀 했었는데..
확실히..다음날 타격이 있더라.. 눈은 떠있어도 뇌가 멈춰버린 느낌😌
이래서 멘토님들께서 무리하지 말라고 하셨나보다. 
하지만 아무리 말해주셔도 귓등으로 듣다가 겪어봐야 아는 나란놈.. 
집에오면 책상앞에서 코딩하다가 새벽밤늦게 맨날 졸았다...
코딩하는것도 아니고 잠을 푹자는것도 아니고 이도저도 아니게 되어버리더라 🥺
다음부턴 페이스 조절 제대로 해야겠다 !!!!!!

<img src=https://media.giphy.com/media/cephYUQtGUORy/giphy.gif width=300>

너무 혼자서만 끙끙 앓지말고 도움을 요청하자!!
개발은 혼자서 해내야 진정 내것이되고 남들이 알려주면 내것이 되지않는다는 생각이 없지않아 있는데
이런생각을 내려놓는것도 좋을것같다. 주변의 도움을 적정선에서 수용하는것이 더 좋은방향이고 보다 더 넓은 시야를 트이게 하는거같다!! 개발은 협업, 팀단위로 하는것인데 굉장히 당연한것을 놓치고있었다니..


실력은 부족하지만 어찌어찌 PM을 맡다보니 맡은일에 대한 책임감도 생기고..
평소에 먼저 나서는 성격도 아니고 기본적으로 좀 내성적인 편이라 책임감이 막중한 역할은 부담스러움을 느껴서 조금 피하는 편이지만, 돌이켜보면 누군가 반드시 해야만하는 일이있는데 아무도 하지않는다면 내키진 않아도 맡아서 했었던거같다. 그렇게 막중한 역할을 맡다보면 끈기와 노력이 부족한 내 자신에게 없던 책임감도 생기고 열심히해야한다는 동기부여도 되고 많은 이점이 있었고 대학시절 과대표도 그렇게 얼떨결에 했었고 미숙했지만 많은걸 배웠고 정말 값지고 좋은 경험이였다.
이번 PM역할도 덥썩 맡게되었지만 많은 시행착오와 미숙함을 느끼며 어떠한 점이 부족했는지에 대해 많이 생각하게되었다. 

<img src=https://thumbs.gfycat.com/BrightNiceAustraliankestrel.webp >

개인적으로 정말 좋아하는 마블 영화의 캐릭터인 가오갤의 피터퀼.

많이 엉성하고 부족하지만 팀을 끝까지 이끌며 유머와 센스가 넘친다.
팀원들도 장난이 넘치지만 팀리더에게 무한신뢰를 보낸다..
비록 영화속 인물이지만 닮고싶은 캐릭터 👏

우리 `Wesop`팀도 많이 부족한 나를 응원도 많이해주고 격려해주고 잘따라와줘서 정말 고맙고 재밌게 프로젝트를 진행했다. 비록 2주간의 프로젝트 팀이였지만 많이 정들어서 2차때도 정말 같이하고싶다 🥲 
중간에 팀원 1명이 개인사로 인해 빠지게되었지만 굴하지않고 더욱 열심히해서 결국 프로젝트를 완수한 `Team Wesop`!!! 정말 2주가 어떻게 지나갔는지 모를정도로 모두 열심히!! 끈기있게 프로젝트를 완수해서 정말 자랑스럽다

- 모두가 피곤하고 지칠만했음에도 항상 분위기를 띄워주고 사기를 북돋아주어 모두가 기분좋게 지속적으로 프로젝트를 진행할수 있게 만들어주셨고 완벽한 로그인, 회원가입 기능을 만들어주시고 자신의 코드를 정말 사랑하는 나르시즘 `원근`님 🤪
- 20기 프론트의 에이스, 항상 질문하러오는사람이 끊이질않고 맡은업무량도 제일 많은데도 싫은티 한번 내지않으시며 친절하게 설명해주시고 끝없이 알려주시고 프로젝트가 끝난뒤에도 팀원들의 코드 이해를 돕기위해 주석까지 계속 작성해주시는 스승 도실버 `도은`님 🤗
- 처음부터 끝까지 항상 친절하시고 팀원들을 매번 챙겨주시며 웃음을 잃지않으시며 맡은일은 밤낮으로 끝까지 노력하며 완수해내주시고 원근님의 근본없는 드립도 다 받아주시는 20기의 친절왕 무한친절 리액션 `미화`님 😇
- 진지하고 또 진지하고 또 진지하지만 그것이 매력이고 프로젝트 기간이 지날수록 장난도 치시고 진지함에서 나오는 장난이 굉장히 웃긴ㅋㅋㅋㅋ 항상 부족하다고 자책하시지만 결국엔 노력으로 모든걸 커버치시며 프로젝트를 성공하신 노력파 진지남 `성호`님 😎





<img src=https://media.giphy.com/media/PwQqd5Q9qxpYs/giphy.gif width=400>

2주동안 모두 잠도 부족하고 안풀리는 문제를 머리싸매고 계속 코딩하느라 많이 힘들법한데도 힘든티 내지않고 시간이 훅 지날만큼 흥미롭게 프로젝트를 진행하게해주어서 정말 감사한 마음..
정말 어떻게 지나갔는지 모르는 2주였지만 정말 재밌었고 마음에와닿는 팀이다 😋
추억으로만 남지않고 앞으로도 계속 이어 갈수 있는, 
수료후에도 다같이 스터디와 프로젝트를하며 쭉 이어가고 싶을정도로 정말 다정하고 좋은팀이였다😗

남는건 동기다 !!!!!!😭😭😭😭😭😭😭😭

<img src=https://user-images.githubusercontent.com/58321429/119234772-83608380-bb6a-11eb-8089-9c0006af7f40.png width=200 height=200>

> Designed By Dosilv in Wesop

