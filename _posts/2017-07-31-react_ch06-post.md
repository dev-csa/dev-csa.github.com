---
layout: post
title: "[React] About Router "
excerpt: "React ch.06"
categories: [React Tutorial]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---

# React ch.06 _ React Router

### 라우팅이란?

  페이지 주소에 따라 원하는 것을 보여주는 것.


  리엑트에 라우터가 내장되어 있는 것은 아님.
  직접 만들어서 사용할 수 있다.

### react-router

  써드파티 라이브러리 이지만, 거의 공식이나 다름없는 ***react-router***


### SPA (Single Page Application)

  전통 웹 구조인 SPA 구조는 유저가 요청을 할 때마다 HTML 을 새로 불러오고 새로고침이 된다.


### react-router 를 이용하여

  처음에 한번 html 을 불러오고 그 이후 요청은 필요한 데이터만 불러와서 자바스크립트를 통해 이를 화면에 뿌려주는 것이다.
  > 유저 인터랙션이 많고 동적인 사이트에 적합


즉, react-router를 사용하는 프로젝트에서는 어떤 경로로 들어오든 똑같은 html파일과 자바스크립트 파일을 제공하며

여기서 제공되는 js 파일에서는 웹 어플리케이션에서 사용 할 모든 컴포넌트들이 담겨있고, URL에 따라서 지정된 컴포넌트를

렌더링 해준다.

그리고 페이지가 한번 로드 된 다음에 다른 페이지로 이동시에는 ***페이지를 처음부터 로딩하지 않고*** 기존에 불러왔던

자바스크립트 파일을 이용 하여 페이지에서 기존 컴포넌트를 언마운트 시키고 다른 컴포넌트를 마운트 함으로써

요청을 처리한다.


참고: https://velopert.com/2937
