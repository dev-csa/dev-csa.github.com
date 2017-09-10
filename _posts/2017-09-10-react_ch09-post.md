---
layout: post
title: "[React] Email 주소 확인하고 입력받는 컴포넌트 만들기"
excerpt: "React ch.09"
categories: [React Tutorial]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---

# React ch.09

## name, email주소 를 확인하고 입력받는 form을 가진 컴포넌트 만들기 1

0. react-skeleton 프로젝트 폴더의 /public/css에 bootstrap.min.css 먼저 복붙해주고 시작


1. 컴포넌트 컨테이너를 만든다.

    src/components/LeadCapture.jsx

    ```typescript jsx
    var React = require('react');

    var LeadCapture = React.createClass({
        render: function() {
            return (
                <div className="col-sm-3">
                    <div className="panel panel-default">
                        <div className="panel-body">

                        </div>
                    </div>
                </div>
            );
        }
    });

    module.exports = LeadCapture;

    ```

2. email 입력 컴포넌트 생성

    src/components/EmailField.jsx

    ```typescript jsx
    var React = require('react');
    var validator = require('email-validator');

    var EmailField = React.createClass({
        getInitialState: function () {
            return{valid: true, value: ""}
        },

        onChange: function (e) {
            var val = e.target.value;

            if (validator.validate(e.target.value)){
               this.setState({valid:false, value: e.target.value})
            } else {
                this.setState({valid: true, value: e.target.value});
            }
        },

        render: function(){
            var formClass = this.state.valid ? "form-group" : "form-group has-error"
            return (
                <div className={formClass}>
                    <input className="form-control" onChange={this.onChange} placeholder="Email" value={this.state.value}/>
                </div>
        );

        }
    });


    module.exports = EmailField;

    ```

    유효한 email인지 확인해주는 모듈인 email-validator 설치

        onChange: function (e) {
            var val = e.target.value;
        },

        에서의 value는 input 의 onChange 에 입력되는 value 값이고,


        getInitalState: function () {
                return{valid: true, value: ""}
            }

        에서의 value는 input의 "value={this.state.value}" 에 value값이다.


3. src/main.jsx 에 컴포넌트 추가

    ```typescript jsx
    var React = require('react');
    var ReactDOM = require('react-dom');
    var EmailField = require('./components/EmailField.jsx');


    ReactDOM.render(<EmailField />, document.getElementById('email'));


    ```           

4. public/index.html 수정

    ```html

    <!DOCTYPE html>
    <html>
        <head>
            <title>CommonJS React Skeleton</title>
            <link rel="stylesheet" href="css/bootstrap.min.css">
            <link rel="stylesheet" href="css/bootstrap-theme.min.css">

        </head>
        <body>
            <div id="email">
            </div>
        <script src="js/main.js"></script>
        </body>
    </html>

    ```

5. 실행결과

    XXX@XXX.c 까지 입력하면 valid email로 인식해서 input box 테두리가 빨간색에서 파란색이 됨.

    <img src="https://cdn-images-1.medium.com/max/2000/1*bgs49E8yND0UGQGRYm_oug.png">

    <img src="https://cdn-images-1.medium.com/max/2000/1*3DpGBNF0Ef5J3uz3NNKsFg.png">
