---
layout: post
title: "[Node] View engine을 이용한 응답처리 "
excerpt: "Node ch.03"
categories: [Node Tutorial]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---

# Node ch.03 _ View engine을 이용한 응답처리

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

    위 코드의 ejs를 랜더링 해주는 부분을 살펴보면,

    ` res.render('email.ejs', {'email' : req.body.email}) `

    /views/email.ejs 로 경로까지 지정하는것이 아니라 email.ejs 만 입력해 준 것을 확인할 수 있다.

    view engine을 사용하면, 알아서 /views/XXX.ejs 경로에 위치한 .ejs 파일을 랜더링 하므로, 파일이름만 입력해주면 된다.



* 실행 결과 확인

<img src="https://cdn-images-1.medium.com/max/600/1*tu1iNFpRtRuSW0f4pMjrZQ.jpeg">

<img src="https://cdn-images-1.medium.com/max/600/1*K6v2GmkgS7JhmzpdswoHjA.jpeg">
