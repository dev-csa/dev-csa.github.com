---
layout: post
title: "[React] React 시작하기"
excerpt: "React ch.01"
categories: [React Tutorial]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---

# React ch.01

## React 시작하기

* IDE 는 ATOM 을 사용할것이므로 패키지를 설치한다

  language-babel 패키지 설치

* React를 사용하기 위해 Node.js를 설치한다.

  `$ npm install readline-sync`
(node module exports 부분 node 에 다시 정리하기)

### 실습에 사용할 npm packages

* browserify

  `$ npm install -g browserify`

  브라우저에서 npm 모듈을 사용할 수 있도록 허용

* babel

  `$ npm install --save-dev babel-cli babel-preset-env`

  Javascript 컴파일을 readable하게 도와주는 모듈


* babel / babelify

  https://github.com/babel/babelify

  babel모듈의 jsx컴파일을 돕는 모듈


* babel-preset-react

  https://www.npmjs.com/package/babel-preset-react

  `$ npm install --save-dev babel-cli babel-preset-react`

  browserify모듈이 babel을 사용하도록 허용하는 모듈


* watchify
  https://github.com/substack/watchify

  컴파일 유용하게 돕는 모듈
