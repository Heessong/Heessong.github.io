---
title : 'Array.method'
date : 2021-04-24 03:19:22
category : 'Javascript'
draft : false
---

>  # Array.method

### 요소를 추가, 제거

- arr.push(...items) : 맨 끝에 요소 추가 
- arr.unshift(...items) : 맨 앞에 요소 추가
- arr.pop() : 맨 끝 요소 제거
- arr.shift() : 맨 앞 요소 제거
- splice(pos, deleteCount,...items) : 시작점 `pos`부터 `deleteCount`개수만큼의 요소를 지우고 `items`를 추가하기
- slice(start,end) : `start` 부터 `end` 의 **바로 앞** 까지의 요소를 복사해 **새로운 배열 생성**
- concat(...items) : 배열의 모든 요소를 복사하고 `items` 를 추가하여 새로운 배열을 만든후 이를  return  , 만약 `items` 가 배열이면 `items` 배열의 요소들을 기존 배열에 추가

### 원하는 요소 찾기

### 원하는 요소 찾기

- indexOf / lastIndexOf(item,pos) : `pos`부터 원하는 `item` 을 찾고, 찾으면 해당요소의 **인덱스** 를, 못찾으면 `-1`을 return
- includes(value) : 배열에 `value` 가 있으면 `true` 아니면 `false` return
- find/filter(func) : 주어진 함수의 조건을 통과하는 **모든 요소**를 모아 새로운 **배열**로 return
- findIndex(func) : 주어진 함수의 조건을 통과하는 **첫번째 요소** 의 **인덱스**를 return 

### 배열안의 전체요소 순회

- forEach(func) : 주어진 함수를 배열 요소 **각각**에 대해 실행

### 배열 변형하기

- map(func) : 숫자의 배열을 받아 각 숫자들의 제곱근이 들어있는 새로운 배열을 만듭니다
- sort(func) : 
- reverse() : 
- split / join : 
- reduce(func,initial) : 



**sort, reverse, splice는 기존의 배열을 변형시킨다**