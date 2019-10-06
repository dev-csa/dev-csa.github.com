---
layout: post
title: "자바스크립트에서 알아둬야 할 핵심 컨셉 - 2"
excerpt: "Things to know about javascript - 2"
categories: [Javascript]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---


>출처: https://github.com/leonardomso/33-js-concepts (노마드코더 영상보고 정리)

## DOM (Document Object Module)

자바스크립트는 html 요소들을 DOM형태로 변경 가능 하다 (객체단위로 접근해서 갖고놀수있다)
`console.log(document);`

<img src="https://miro.medium.com/max/1118/1*O31VV7G3O8Zpg0kyo2v-tw.png" />


```javascript

    //const title = document.getElementById("title");   // id 가 title인 객체 select
    const title = document.querySelector("#title");     // id 가 title인 객체 select
    const title2 = document.querySelector(".title2");   // class 가 title2인 객체 select
    console.dir(title);

```
`console.dir(title)`을 실행해서 콘솔창에서 살펴보면 접근할 수 있는 객체들을 모두 확인할 수 있다.

<img src="https://miro.medium.com/max/1072/1*bojzXIAT_GA4NfL60tVXdA.png" />



## Event & Event handler

```javascript
    function handleResize(event){
        console.log(event);
    }
    window.addEventListener("resize", handleResize);

```

위 코드에서 event는 어디서 왔는가? 무엇을 지칭하나?
: 자바스크립트에서 왔다.
이벤트를 다룰 함수를 만들때 마다, 자바스크립트는 자동적으로 함수를 객체에 붙인다.

저 코드를 실행하면, 인터넷창이 resize될때마다 이벤트 객체가 호출된다.

<img src="https://miro.medium.com/max/1174/1*oy5kVwi5mPziqpXxQBlbkg.png">

### javacript dom event mdn

이벤트의 근원을 알고싶으면 MDN을 살펴보자
