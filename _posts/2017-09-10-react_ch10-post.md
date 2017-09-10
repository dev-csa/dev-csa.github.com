---
layout: post
title: [React] Email 주소 확인하고 입력받는 컴포넌트 만들기 2 
excerpt: "React ch.10 "
categories: [React Tutorial]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---

# React ch.10

## name, email주소 를 확인하고 입력받는 form을 가진 컴포넌트 만들기 2

#### EmailField 에 이어 NameField 컴포넌트 생성

1. src/components/NameField.jsx 생성
    
    ```typescript jsx
    var React = require('react');
    
    var NameField = React.createClass({
    
        getInitialState: function () {
            return {value: ""}
        },
    
        onChange: function (e) {
            this.setState({value: e.target.value});
        },
    
        render: function () {
    
            return(
                <input className="form-control"
                       placeholder={this.props.type + " Name"}
                       onChange={this.onChange}
                       value={this.state.value} />
    
            );
        }
    });
    
    module.exports = NameField;
    
    ```
    
2. LeadCapture 에서 name과 email 컴포넌트 처리할 수 있도록 src/components/LeadCapture.jsx 수정

    ```typescript jsx
    var React = require('react');
    var EmailField = require('./EmailField.jsx');
    var NameField = require('./NameField.jsx');
    
    var LeadCapture = React.createClass({
        onSubmit: function (e) {
          // 아래 render에 ref가 요기로 들어오고 여기서 valid 된 값은 EmailField.jsx로 간다
            if (!this.refs.fieldEmail.state.valid){
              alert("Email is always required!")
          } else {
              // 서버 or 호스트로 request send
              var httpRequestBody = {
                  email: this.refs.fieldEmail.state.value,
                  firstName: this.refs.fieldName.state.value
              };
          }
    
        },
    
        render: function() {
            return (
                <div className="col-sm-3">
                    <div className="panel panel-default">
                        <div className="panel-body">
                            <NameField type="first" ref="fieldName"/>
                            <EmailField ref="fieldEmail" />
                            <button className="btn btn-primary" onClick={this.onSubmit}>Submit</button>
                        </div>
                    </div>
                </div>
            );
        }
    });
    
    module.exports = LeadCapture;
    ```    
    
3. src/main.jsx 수정

    ```typescript jsx
    var React = require('react');
    var ReactDOM = require('react-dom');
    var LeadCapture = require('./components/LeadCapture.jsx');
    
    ReactDOM.render(<LeadCapture />, document.getElementById('leadCapture'));

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
            <div class="container">
                <div id="leadCapture"></div>
            </div>
        <script src="js/main.js"></script>
        </body>
    </html>

    ```    
    
5. 실행결과 확인

    invalid email 입력
    
    <img src="https://cdn-images-1.medium.com/max/2000/1*3WhkCTp6WNttpKg1eeRXpA.png">
    
    <img src="https://cdn-images-1.medium.com/max/2000/1*XWetZgPJmN3ngsOu-efTFA.png">
    
    valid email 입력
    
    <img src="https://cdn-images-1.medium.com/max/800/1*tPaUbTO17r9JCE42ikwNyw.png">
    
    
6. invalid email을 입력했을 땐 메세지창을 보여줬으니 valid email을 submit 했을 땐 input box를 clear 시켜보자

    EmailField.jsx 수정 (claer 함수 추가)
    
    ```typescript jsx
    var React = require('react');
    var validator = require('email-validator');
    
    var EmailField = React.createClass({
        getInitialState: function () {
            return{valid: true, value: ""};
        },
    
        onChange: function (e) {
            var val = e.target.value;
    
            if (!validator.validate(e.target.value)){
               this.setState({valid:false, value: e.target.value})
            } else {
                this.setState({valid: true, value: e.target.value});
            }
        },
        clear: function () {
            this.setState({valid: true, value: ""});
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
    
    NameField.jsx 수정 (claer 함수 추가)
    
    ```typescript jsx
    var React = require('react');
    
    var NameField = React.createClass({
    
        getInitialState: function () {
            return {value: ""}
        },
    
        onChange: function (e) {
            this.setState({value: e.target.value});
        },
    
        clear: function () {
          this.setState({value: ""});
        },
    
        render: function () {
    
            return(
                <input className="form-control"
                       placeholder={this.props.type + " Name"}
                       onChange={this.onChange}
                       value={this.state.value} />
    
            );
        }
    });
    
    module.exports = NameField;        
    ```
    
    LeadCapture.jsx 수정
    
    ```typescript jsx
    var React = require('react');
    var EmailField = require('./EmailField.jsx');
    var NameField = require('./NameField.jsx');
    
    var LeadCapture = React.createClass({
        onSubmit: function (e) {
          // 아래 render에 ref가 요기로 들어오고 여기서 valid 된 값은 EmailField.jsx로 간다
            if (!this.refs.fieldEmail.state.valid){
              alert("Email is always required!")
          } else {
              // 서버 or 호스트로 request send
              var httpRequestBody = {
                  email: this.refs.fieldEmail.state.value,
                  firstName: this.refs.fieldName.state.value
              };
    
              this.refs.fieldName.clear();
              this.refs.fieldEmail.clear();
    
          }
    
        },
    
        render: function() {
            return (
                <div className="col-sm-3">
                    <div className="panel panel-default">
                        <div className="panel-body">
                            <NameField type="first" ref="fieldName"/>
                            <br />
                            <EmailField ref="fieldEmail" />
                            <button className="btn btn-primary" onClick={this.onSubmit}>Submit</button>
                        </div>
                    </div>
                </div>
            );
        }
    });
    
    module.exports = LeadCapture;

    ``` 
    

7. LeadCapture 컴포넌트 활용하기 

   Email과 name을 입력받는 컴포넌트인 LeadCapture 컴포넌트를 그냥 copy&paste 함으로써 쉽게 활용할 수 있다
   
   한 페이지에서 3쌍의 Email, Name을 받아오기
   
   main.jsx 수정 
   
   ```typescript jsx
   var React = require('react');
   var ReactDOM = require('react-dom');
   var LeadCapture = require('./components/LeadCapture.jsx');
   
   ReactDOM.render(<LeadCapture />, document.getElementById('leadCapture'));
   ReactDOM.render(<LeadCapture />, document.getElementById('leadCapture1'));
   ReactDOM.render(<LeadCapture />, document.getElementById('leadCapture2'));


    ```

    index.html 수정
    
    ```html
    <!DOCTYPE html>
    <html>
        <head>
            <title>CommonJS React Skeleton</title>
            <link rel="stylesheet" href="css/bootstrap.min.css">
            <link rel="stylesheet" href="css/bootstrap-theme.min.css">
    
        </head>
        <body>
            <div class="container">
                <div id="leadCapture"></div>
                <div id="leadCapture1"></div>
                <div id="leadCapture2"></div>
            </div>
        <script src="js/main.js"></script>
        </body>
    </html>

    ```

8. 결과 확인 

    <img src="https://cdn-images-1.medium.com/max/1600/1*RcZh104cwBxiYnmj7bW_ow.png">