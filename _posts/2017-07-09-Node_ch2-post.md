---
layout: post
title: Node ch.2
excerpt: "[Node] POST 요청 처리"
categories: [Node 강좌 따라하기]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---

# Node ch.2

### POST 요청 처리
* /pubilc/form.html 생성

    {% highlight html %}
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

    {% endhighlight %}

* 구동확인

    localhost:3000/form.html

* email_post 라우팅 처리 ::app.js 수정

    {% highlight javascript %}
    app.post('/email_post', function(req,res){
    	res.send("post response")
    })
    {% endhighlight %}

* post방식으로 값을 받아오려면 bady-parser 모듈을 설치해줘야함

    `$ npm install body-parser --save`

* app.js 에 모듈 등록

    {% highlight javascript %}
    var bodyParser = require('body-parser')
    {% endhighlight %}

* post 로 값을 받아오는 형식 지정 :: app.js

    {% highlight javascript %}
    app.use(bodyParser.json())
    app.use(bodyParser.urlencoded({extended:true}))
    {% endhighlight %}


* 받아온 값 사용 (여기선 email) :: app.js

    {% highlight javascript %}
    app.post('/email_post', function(req,res){
    	console.log(req.body.email)
    	res.send("post response")
    })
    {% endhighlight %}

* 받아온 값을 화면에 보여주기 :: app.js
    {% highlight javascript %}
    app.post('/email_post', function(req,res){
    	console.log(req.body.email)
    	res.send("<h1>Welcome!" + req.body.email + "</h1>")
    })
    {% endhighlight %}


* 여기까지의 실행 화면 보기

<img src="https://cdn-images-1.medium.com/max/400/1*lN38sJpDyL-yBmerTc7CKg.jpeg">

<img src="https://cdn-images-1.medium.com/max/400/1*CuDWuFI4tQ_WTggcV-S1hg.jpeg">

<img src="https://cdn-images-1.medium.com/max/400/1*V2RTHgGWTDZ6XqWpq28KIg.jpeg">



### View engine을 이용한 응답처리
##### ejs나 jade와 같은 템플릿 엔진을 활용해 view 템플릿을 활용해 응답 할 수 있다


* ejs 모듈 설치

    `$ npm install ejs --save`

    pakage.json에 자동 업데이트 된다.

* 모듈 사용해서 나타내기 :: app.js

    {% highlight javascript %}
    app.set('view engine', 'ejs')
    {% endhighlight %}
* /views 경로 생성, /views/email.ejs 파일 생성

    {% highlight html %}
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

    {% endhighlight %}

* email.ejs를 사용하려면 :: app.js

    {% highlight javascript %}
    var express = require('express')
    var app = express()
    var bodyParser = require('body-parser')

    app.listen(3000, function() {
      console.log("start@ on port 3000");
    });

    app.use(express.static('public'))
    app.use(bodyParser.json())
    app.use(bodyParser.urlencoded({extended:true}))
    app.set('view engine', 'ejs')


    app.get('/', function(req,res){
      console.log('test');
      res.sendFile(__dirname + "/public/main.html")
    })

    app.get('/main', function(req,res){
      res.sendFile(__dirname + "/public/main.html")
    })

    app.post('/email_post', function(req,res){
      console.log(req.body.email)
      //res.send("<h1>Welcome!" + req.body.email + "</h1>")
      res.render('email.ejs', {'email' : req.body.email})
    })


    {% endhighlight %}


* 실행 결과 확인

<img src="https://cdn-images-1.medium.com/max/600/1*tu1iNFpRtRuSW0f4pMjrZQ.jpeg">

<img src="https://cdn-images-1.medium.com/max/600/1*K6v2GmkgS7JhmzpdswoHjA.jpeg">
