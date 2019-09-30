---
layout: post
title: "자바스크립트에서 알아둬야 할 핵심 컨셉"
excerpt: "Things to know about javascript"
categories: [Javascript]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---


>출처: https://github.com/leonardomso/33-js-concepts (노마드코더 영상보고 정리)

## Call stack
자바스크립트가 함수 실행을 핸들하는 방법 중 하나

함수가 실행되면, 스택 리스트에 쌓고, 실행이 완료되면 함수는 리스트에서 제거된다. 에러가 있을 경우 해당 함수는 리스트에서 제거되지 않고 에러를 보여준다.


## Value Types and Reference Types

- value의 경우

```javascript
  let a = 50;
  let b = a;

  a = 10;
  console.log(b);
  // 50출력됨.

```

- reference의 경우

```javascript
  const cat = ["Thor", "Lime"];
  const cute = cat;

  cat.push("Lala");
  console.log(cute);
  // ['Thor', 'Lime', 'Lala'] 출력됨.
```

값을 복사하는 것이 아니라 배열을 "참조" 하기때문에 업데이트를 하지 않아도 cute가 cat을 그대로 참조한 값을 출력하게 된다. 이때 참조라는 것은 해당 배열을 가르키는 메모리를 동일하게 가르킨다는 뜻.

그러므로,
console.log([10] === [10]);
은 False를 출력하게 된다.
다른 서로 다른 메모리에 위치해 있기 때문에!!


## Type coercion(conversion)
```javascript
console.log(66 + true) // 67
console.log(66 + "Thor") // 66Thor
console.log(66 + 10 + "Thor") // 76Thor

```


## ==와 ===의 차이
```javascript
console.log("1" == 1);
//true type conversion이 일어남
console.log("1" === 1);
// False conversion 일어나지 않음
```
=== 쓰는것이 버그를 피해갈 수 있음!

## js는 none blocking 언어이다.

blocking된다는 것이 무엇이냐? 말 그대로 진행이 막히는 것인데
예를들면 js의 alert() 가 블로킹 펑션이기 때문에 alert()로 경고창이 뜨면, 아무 작업도 할 수 없고
경고창을 꺼야만 다음 작업이 진행되는 것이다.
js가 blocking 언어였다면 아무것도 할 수 없다는 뜻..
그대신 event, callbacks 을 이용해서 작업을 처리하니까 none blocking으로 해결할 수 있다.


## Expression vs Statement

- Expression

Expression returns a value
value를 리턴하는 것 = expression

예)
```javascript
function add(a,b){
return a + b;
}

const how = add(5, 6);
// = const how = 11; <<< 함수가 리턴하는 것!
```


- Statement

명령 혹은 지시

```javascript
const thing = if(true){

}

console.log(if(true(){});
````

위 둘 다 에러임. 값이 아니라서 오류.
저 자리에는 expression이 들어가야함


## IIFE

Immediately-Invoked function Expression
함수. 자기자신을 부르는 함수.

예) 함수를 만들고 부른다.
```javascript
(function(){
const secretUsers = ["aa", "bb", "cc"];
console.log(secretUsers);
})()
```

이렇게 하면 웹 콘솔창에서 secretUsers로 선언된 애들이 보이지 않게된다!! 즉, 숨길 수 있다는 것! 클라이언트가 접근이 불가능해서 수정할 수 없게된다.
