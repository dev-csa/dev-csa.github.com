---
layout: post
title: React ch.05
excerpt: "[React] Tips for React "
categories: [React Tutorial]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---

# React ch.04

## Tips for React

* React로 웹페이지 설계하기

  React 공식 웹사이트

  https://facebook.github.io/react/ 에서 Thinking in React 활용한다.

  기능들을 어떤식으로 컴포넌트로 쪼개나갈지를 생각하면서 설계한다.

  React는 최대한 모든 기능들을 쪼개어 component로 만들어서 사용하는것이 좋다.

  일단 하나의 큰 컴포넌트를 만들고 기능별로 쪼개나가는 것도 하나의 방법이다.


* 크롬 React Developer Tool

  https://chrome.google.com/webstore/search/react%20developer%20tools?hl=ko

  설치하여 사용하기


* Autobinding & 'this'

  React 에는 this가 없다!
  > javascript와는 다르게 React에서는 모든 메서드 들이 컴포넌트 인스턴스들과 자동으로 바인드 되어 this 키워드를 사용할 필요가 없다.

* React는 virtual DOM 을 사용한다.
  > 그래서 빠르다.


* Event system in React

  참고 사이트: https://facebook.github.io/react/docs/events.html
