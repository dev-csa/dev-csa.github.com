---
layout: post
title: "[React] 기초"
excerpt: "Learning React "
categories: [React Fundamental]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---

## React 기초 

React.js는 페이스북 엔지니어가 개발한 자바스크립트 라이브러리 이다.

다양한 이유로 널리 사용되고 있으므로 공부해보려고 함.


일단 코드로 살펴보자!

```javascript
    const h1 = <h1>Hello world</h1>;
```

위 코드는 자바스크립트처럼 보인다. 또한 h1 태그가 보이는걸로 봐서 html 코드 같기도 하다.

하지만, 이 코드는 html 에서도 javascript 에서도 독자적으로 동작하지 않는다.


```
<h1>Hello world</h1>
``` 
위 h태그 부분이 jsx 코드이다.

jsx는 자바스크립트이 확장형 문법이지만 컴파일 작업을 통해야만 자바스크립트로 작동할 수 있다. 
<br/>

즉, jsx는 html처럼 생겼지만 자바스크립트 파일에서 볼 수 있는 코드라고 보면 된다.

또한 생긴건 html이지만 자바스크립트 문법을 사용해 표현된다.

그렇기 때문에 jsx는 변수도 만들 수 있고 함수, 배열, 객체 등을 자바스크립트의 문법에 따라 만들 수 있다.

<br/><br/>

#### Example: jsx코드의 객체 선언  
```
const myTeam = {
  center: <li>Benzo Walli</li>,
  powerForward: <li>Rasha Loa</li>,
  smallForward: <li>Tayshaun Dasmoto</li>,
  shootingGuard: <li>Colmar Cumberbatch</li>,
  pointGuard: <li>Femi Billon</li>
};
```
<br/><br/>

뿐만아니라 html요소들을 자유자재로 다룰 수 있다.

#### Example: jsx코드의 html 태그 사용 
```
<a href="http://www.example.com">Welcome to the Web</a>;

const title = <h1 id="title">Introduction to React.js: Part I</h1>;

const panda = <img src="images/panda.jpg" alt="panda" width="500px" height="500px" />;
```
<br/>

중첩된 html 코드를 하나의 변수로 선언하는 것도 가능하다.
#### Example: jsx코드의 html 태그 사용2
```
const theExample = (
   <a href="https://www.example.com">
     <h1>
       Click me!
     </h1>
   </a>
 );
```


이것으로 jsx코드의 모습을 살펴봤다면, 다음 포스팅에서 어떻게 랜더링시키는지 확인해보자.