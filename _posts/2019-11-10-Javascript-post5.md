---
layout: post
title: " JS 로 간단한 그림판 만들기 "
excerpt: ""
categories: [Javascript]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---

## JS로 간단한 웹 그림판을 만들어보자

MDN 에서 canvas rendering 살펴보기
https://developer.mozilla.org/en-US/docs/Web/API/CanvasRenderingContext2D


```javascript

  const canvas = document.getElementById("jsCanvas");
  const cxt = canvas.getContext("2d");

  canvas.width = 700;
  canvas.height = 700;

```

여기서 실수하지 말아야 할 것은,
stylesheet 에서 canvas 사이즈를 설정했다고 해도, js 코드에서도 사이즈를 지정 해 주어야한다.
디자인 부분에 해당하는 사이즈와, 픽셀을 가져와서 사용할 사이즈를 설정하는 것.
