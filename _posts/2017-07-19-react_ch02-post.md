---
layout: post
title: "[React] React 프로젝트 시작하기"
excerpt: "React ch.02"
categories: [React Tutorial]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---

# React ch.02

## React 프로젝트 시작하기

1. 새로운 프로젝트 경로 생성

    `$ mkdir react-skeleton`

    `$ cd react-skeleton`

    `$ mkdir public`

    `$ mkdir src`




2. `$ npm init`

    npm init 실행하면 프로젝트를 생성하면서 프로젝트에 해당하는 정보를 이것저것 물어보는데,

    그냥 모두 엔터 쳐서 완료시킨다.

    npm init 이 완료되면 package.json파일이 자동으로 생성됨.


3. 프로젝트에 사용할 패키지 install

    `$ npm install -g browserify`

    `$ npm install --save babelify`

    `$ npm install --save watchify`

    `$ npm install --save babel-preset-react`

    `$ npm install --save react`

    `$ npm install --save react-dom`



4. src/components 폴더 생성


5. src/components/main.jsx 파일 생성

    ```js

    var React = require('react');
    var ReactDOM = require('react-dom');
    var List = require('./components/List.jsx');

    ReactDOM.render(<List />, document.getElementById('ingredients'));
    ```

6. src/components/List.jsx 파일 생성

    ```js

    var React = require('react');
    var ListItem = require('./ListItem.jsx');

    var ingredients = [{"id":1, "text":"ham"},
    {"id":2, "text":"cheese"}, {"id":3, "text":"potatoes"}];

    var List = React.createClass({
      render: function(){
        var listItems = ingredients.map(function(item) {
          return <ListItem key={item.id} ingredient={item.text} />;
        });

        return (<ul>{listTimes}</ul>);
      }
    });


    module.exports = List;
    ```


7. src/components/ListItem.jsx 파일 생성

    ```js

    var React = require('react');
    var ListItem = React.createClass({
      render: function() {
        return (
          <li>
            <h4>{this.props.ingredient}</h4>
          </li>
        )
      }
    });


    module.exports = ListItem;
    ```


8. public/index.html 파일 생성

    ```html

    <!DOCTYPE html>
    <html>
      <head>
        <title>CommonJS React Skeleton </title>
      </head>
      <body>
        <div id="ingredients">
        </div>
      <script src="js/main.js"></script>
      </body>
    </html>
    ```


9. public/js/main.js js경로에 main.js파일 생성

    후에 npm start 하면 자동으로 코드가 생성된다. 파일만 생성해 두면 됨


10. package.json 파일 수정 > 설치한 패키지들을 사용하기 위해서

    ```json
    
    {
      "name": "react-skeleton",
      "version": "1.0.0",
      "description": "",
      "main": "index.js",
      "scripts": {
        "start": "watchify src/main.jsx -v -t [ babelify --presets [ react ] ] -o public/js/main.js",
        "test": "echo \"Error: no test specified\" && exit 1"
      },
      "repository": {
        "type": "git",
        "url": "git+https://github.com/dev-csa/react-skeleton.git"
      },
      "author": "",
      "license": "ISC",
      "bugs": {
        "url": "https://github.com/dev-csa/react-skeleton/issues"
      },
      "homepage": "https://github.com/dev-csa/react-skeleton#readme",
      "dependencies": {
        "babel-preset-react": "^6.24.1",
        "babelify": "^7.3.0",
        "react": "^15.6.1",
        "react-dom": "^15.6.1",
        "watchify": "^3.9.0"
      }
    }
    ```

    scripts 항목에 ***"start": "watchify src/main.jsx -v -t [ babelify --presets [ react ] ] -o public/js/main.js"***
    를 추가함으로써, jsx파일의 수정사항을 watchfiy 패키지로 즉각 반영하고, babelify 패키지로 jsx형식의 코드를 js코드로 변환(?) 해줄 수 있게 되었다.

11. `$ npm start`

12. mian.js파일이 자동으로 수정됨을 확인.

13. 화면 출력 확인
