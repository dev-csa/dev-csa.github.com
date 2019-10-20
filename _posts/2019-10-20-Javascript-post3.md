---
layout: post
title: "Javascript 함수 & Props 정리 "
excerpt: ""
categories: [Javascript]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---


<바닐라 자바스크립트 강의에서 사용 한 함수와 프로퍼티 정리>

## Date() 와 setInterval()
setInterval() 함수를 이용하여 화면 새로고침 없이 날짜와 시간의 변화를 확인 할 수 있다.


```javascript

  const clockContainer = document.querySelector(".js-clock");
  const clockTitle = clockContainer.querySelector("h1");

  function getTime(){
    const date = new Date();
    const hours = date.getHours();
    const minutes = date.getMinutes();
    const seconds = date.getSeconds();

    clockTitle.innerText = `${hours < 10 ? `0${hours}` : hours}:${minutes < 10 ? `0${minutes}`: minutes}:${seconds < 10 ? `0${seconds}` : seconds}`;
  }

  function init(){
    getTime();
    setInterval(getTime, 1000) ;
  }

  init();

```

## classList 프로퍼티
classList 프로퍼티를 이용하여 Javascript DOM 객체의 class를 쉽게 조작할 수 있다.

- add() : class 이름 추가
- remove() : class 이름 삭제
- toggle(): class 이름 토글
- 이 외에도 더 있음.

```javascript

  const form = document.querySelector(".js-form");
  form.classList.remove("showing");
  form.classList.add("showing");

```


## localStorage 이용하여 클라이언트에 데이터 저장하기
- setItem() : 데이터 저장
- getItem() : 데이터 불러오기
- removeItem() : 객체에서 원하는 값 삭제
- clear() : 저장된 모든 항목 삭제

``` javascript

  localStorage.setItem(key, value);
  // 혹은 localStorage.setItem.key = value;
  // 위 두가지 형식으로 데이터 저장&불러올 수 있다
  localStorage.getItem(key);

```

또한 객체형태로도 저장하고 사용이 가능한데, 이를위해선 JSON형식을 변환해줘야한다.
입력할 때 JSON.stringify(), 가져올 때 JSON.parse()

```javascript

  const toDoObj = {
    text: text,
    id: newId
  };
  toDos.push(toDoObj);
  saveToDos();

  function saveToDos() {
    localStorage.setItem('toDos', JSON.stringify(toDos));
  }

  function loadToDos() {
  const loadedToDos = localStorage.getItem(TODOS_LS);
  if(loadedToDos !== null){
    const parsedToDos = JSON.parse(loadedToDos);
    parsedToDos.forEach(function(item){
      paintToDo(item.text);
    });
  }

}

```

localStorage에 저장된 데이터 확인하는 방법
 : 개발자도구 - Application - Storage 에서 확인가능

<img src="https://miro.medium.com/max/2356/1*n7NDPj3OB7JQ8QcHXCbb9w.png" />
