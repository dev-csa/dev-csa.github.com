---
layout: post
title: Node ch.1
excerpt: "NPM 프로젝트 시작하기"
categories: [hello world]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---

# Node ch.1

--- npm 프로젝트 시작하기

1. 디렉토리 생성
2. npm init
3. express 웹서버를 사용할거임
  npm node install express --save
  (package.json 에서 확인가능)

4. app.js 생성

  ```
  var express = require('express')
  var app = express()
  app.listen(3000, function() {
  	console.log("start@ on port 3000");
  });

  console.log("end if server code...");
  ```

5. node app.js
  localhost:3000 < 서버 구동 확인

6. nodemon 설치 (수정 사항 감지해서 자동 업데이트해주는 패키지)
  `sudo npm install nodemon -g`

7. nodemon app.js

--- url routing 처리(GET 요청 처리)
8. app.js 수정

  ```
  var express = require('express')
  var app = express()
  app.listen(3000, function() {
  	console.log("start@ on port 3000");
  });

  app.get('/', function(req,res){
  	res.send("<h1>hi Thor</h1>")
  })
  ```

9. /public/main.html 생성

  ```
  <html>
    <head>
      <meta charset="utf-8">
      <title>main.html</title>
    </head>
    <body>
      <h1>main page </h1>
      <p> lalalalalalal </p>

    </body>
  </html>
  ```

10. 구동확인

  localhost:3000/public/main.html

  위 방법은 잘못된 방법임, 요청을 처리하도록 코드를 입력 해야함 :: res.sendFile()

11. app.js 수정

  ```
  var express = require('express')
  var app = express()
  app.listen(3000, function() {
  	console.log("start@ on port 3000");
  });

  app.get('/', function(req,res){
  	*** res.sendFile(__dirname + "/public/main.html") ***
  })
  ```

--- static 디렉토리 설정
12. app.js 수정
  ```
  app.use(express.static('public'))
  ```

  public 경로 아래에 위치한 파일들을 모두 static으로 요청 받아옴

13. /public/main.js 추가

  ```
  console.log("main js loaded");
  ```

14. main.html 수정

  ```
  !<!DOCTYPE html>
  <html>
    <head>
      <meta charset="utf-8">
      <title>main</title>
    </head>
    <body>
      <h1>main page </h1>
      <p> lalalalalalal </p>
      <script src="main.js"> </script>

    </body>
  </html>
  ```

  main.js 파일을 요청할 수 있게 되었음을 확인

15. /main 으로 접속했을때에도 main.html 화면과 동일하게 나타내기 :: app.js 에 아래 app.get 추가

  ```
  app.get('/main', function(req,res){
  	res.sendFile(__dirname + "/public/main.html")

  })
  ```

  localhost:3000/main  < 으로 화면 확인
  localhost:3000 < 화면과 같은 화면 출력
