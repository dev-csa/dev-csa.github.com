---
layout: post
title: "[React] input값을 받아서 화면에 리스트로 바로 표시하기"
excerpt: "React ch.03"
categories: [React Tutorial]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---

# React ch.03

## input값을 받아서 화면에 리스트로 바로 표시하기

1. 시작하기 1에서 사용했던 react-skeleton 경로로 이동

    List.jsx와 ListItem.jsx파일을 수정한다.

2. react-skeleton/src/components/List.jsx

  react의 goal중 하나는 속도!

  unique identifier를 줌으로써 빠르게 값을 가져올수 있어야 한다.

  **여기선 text, index 에 해당됨**


  ```
  var React = require('react');
  var ListItem = require('./ListItem.jsx');

  var List = React.createClass({
      render: function() {

          var CreateItem = function(text, index) {
              return <ListItem key={index + text} text={text} />;
          };
      }
  })
  ```

3. react-skeleton/src/components/ListItem.jsx

  render는 화면에 나타내는 부분이며

  {}대괄호 내부에는 자바스크립트 코드가 들어간다.


  ```
  var React = require('react');

  var ListItem = React.createClass({
      render: function(){  
          return (
              <li>
                <h4>{this.props.text}</h4>              
              </li>
          );

      }
  })

  module.exports = ListItem;

  ```

  4. react-skeleton/src/components/ListManager.jsx 파일 생성

    ```
    var React = require('react');
    var List = require('./List.jsx');
    //var ReactDOM = require('react-dom');

    var ListManager = React.createClass({
        getInitialState: function() {
            return {items: [], newItemText:''};
        },
        onChange: function(e){
            this.setState({newItemText: e.target.value});
        },
        handleSubmit: function(e) {
            e.preventDefault();

            var currentItems = this.state.items;

            currentItems.push(this.state.newItemText);

            this.setState({items: currentItems, newItemText:''});
        },

        render: function() {
            return(
                <div>
                    <h3>{this.props.title}</h3>
                    <form onSubmit={this.handleSubmit}>
                        <input onChange={this.onChange} value={this.state.newItemText} />
                        <button>Add</button>
                    </form>
                    <List items=this.state.items} />
                </div>
            );
        }
    });


    module.exports = ListManager;

    ```

    Add버튼을 누를 때 마다 `<List items={this.state.item} />` 해당되는 ADD된 리스트가 랜더링 된다.


5. /src/main.jsx 파일 수정

  ```
  var React = require('react');
  var ReactDOM = require('react-dom');
  //var List = require('./components/List.jsx');
  var ListManager = require('./components/ListManager.jsx');

  ReactDOM.render(<ListManager title="Ingredients" />, document.getElementById('ingredients'));

  ```

6. /public/index.html 수정

  ```
  <!DOCTYPE html>
  <html>
      <head>
          <title>CommonJS React Skeleton</title>
      </head>
      <body>
          <div id="ingredients">
          </div>
      <script src="js/main.js"></script>
      </body>
  </html>

  ```

7. `npm start` 화면 확인
