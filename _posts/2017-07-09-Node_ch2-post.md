---
layout: post
title: Node ch.2
excerpt: "[Node] POST 요청 처리"
categories: [hello world]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---

# Node ch.2

### POST 요청 처리
1. /pubilc/form.html 생성

    ```
    <!DOCTYPE html>
    <html>
      <head>
        <meta charset="utf-8">
        <title>email form</title>
      </head>
      <body>
        <form action="/email_post" method="post">
          email : <input type="text" name="email"> <br/>
          submit <input type="submit">
        </form>


      </body>
    </html>

    ```


2. 구동확인

    localhost:3000/form.html

3. email_post 라우팅 처리 ::app.js 수정

    ```
    app.post('/email_post', function(req,res){
    	res.send("post response")
    })
    ```

4. post방식으로 값을 받아오려면 bady-parser 모듈을 설치해줘야함

    `$ npm install body-parser --save`

5. app.js 에 모듈 등록

    ```
    var bodyParser = require('body-parser')
    ```

6. post 로 값을 받아오는 형식 지정 :: app.js

    ```
    app.use(bodyParser.json())
    app.use(bodyParser.urlencoded({extended:true}))
    ```

7. 받아온 값 사용 (여기선 email) :: app.js

    ```
    app.post('/email_post', function(req,res){
    	***console.log(req.body.email)***
    	res.send("post response")
    })
    ```

8. 받아온 값을 화면에 보여주기 :: app.js
    ```
    app.post('/email_post', function(req,res){
    	console.log(req.body.email)
    	res.send("<h1>Welcome!" + req.body.email + "</h1>")
    ```


### View engine을 이용한 응답처리
##### ejs나 jade와 같은 템플릿 엔진을 활용해 view 템플릿을 활용해 응답 할 수 있다


1. ejs 모듈 설치

    `$ npm install ejs --save`

2. 모듈 사용해서 나타내기 :: app.js

    ```
    app.set('view engin', 'ejs')
    ```
3. /views 경로 생성, /views/email.ejs 파일 생성

    ```
    <!DOCTYPE html>
    <html>
      <head>
        <meta charset="utf-8">
        <title>email ejs template</title>
      </head>
      <body>
        <h1>Welcom !! <%= email %> </h1>
        <p>Nice to meet you</p>

      </body>
    </html>

    ```

4. email.ejs를 사용하려면 :: app.js

    ```
    app.post('/email_post', function(req,res){
    	console.log(req.body.email)
    	//res.send("<h1>Welcome!" + req.body.email + "</h1>")
    	res.render('email.ejs', {'email' : req.body.email})
    })
    ```
