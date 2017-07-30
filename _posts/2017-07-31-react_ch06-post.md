---
layout: post
title: React ch.06
excerpt: "[React] Multiple pages with React Router "
categories: [React 강좌 따라하기]
comments: true
image:
  feature:
  credit: thomas shellberg
  creditlink: https://unsplash.com/photos/Ki0dpxd3LGc
---

# React ch.05

## Multiple pages with React Router

1. `cd react-router`  

    react-skeleton프로젝트에서 이름만 바꿈


2. `$ npm install history@1.13.1 react-router@latest`

3. /src/Routes.jsx 생성

    ```
    var React = require('react');
    var ReactRouter = require('react-router');
    var Router = ReactRouter.Router;
    var Route = ReactRouter.Route;


    var Routes = (
      <Router>
          <Route path="/" component={Base} />
            <Route path="/page1" component={Page1} />
            <Route path="/page2" component={Page2} />

     </Router>
    );

    module.exports = Routes;


    ```

4. /src/components/Base.jsx 생성

    ```
    var React = require('react');

    var Base = React.createClass({
      render: function() {
        return (
          <div>
              <h1>Header</h1>
              {this.props.children}
              <h1>Footer</h1>
          </div>
        );
      }
    });


    module.exports = Base;

    ```

5. /src/components/Page1.jsx 생성

    ```
    var React = require('react');

    var Page1 = React.createClass({
      render: function() {
          return (
            <h1> Page 1 </h1>

          );
      }
    });


    module.exports = Page1;

    ```


6. /src/components/Page2.jsx 생성

    ```
    var React = require('react');

    var Page2 = React.createClass({
      render: function() {
          return (
            <h1> Page 2 </h1>

          );
      }
    });


    module.exports = Page2;

    ```  

7. 방금 생성한 Base, Page1, Page2 jsx 파일 import

    Routes.jsx  수정

    ```
    var React = require('react');
    var ReactRouter = require('react-router');
    var Router = ReactRouter.Router;
    var Route = ReactRouter.Route;

    var Base = require('./components/Base.jsx');
    var Page1 = require('./components/Page1.jsx');
    var Page2 = require('./components/Page2.jsx');

    var Routes = (
      <Router>
          <Route path="/" component={Base}>
            <Route path="/page1" component={Page1} />
            <Route path="/page2" component={Page2} />
          </Route>
     </Router>
    );

    module.exports = Routes;


    ```

8. /src/main.jsx 수정

    ```
    var React = require('react');
    var ReactDOM = require('react-dom');
    var Router = require('./Routes.jsx');

    ReactDOM.render(Routes, document.getElementById('main'));

    ```

9. /public/js/index.html 수정

    ```
    <!DOCTYPE html>
    <html>
        <head>
            <title>CommonJS React Skeleton</title>
        </head>
        <body>
            <div id="main">
            </div>
        <script src="js/main.js"></script>
        </body>
    </html>


    ```


10. `$ npm start`

  아직 화면은 빈 화면.. npm kill 하고 아래 명령 입력

11. `$ npm install -g http-server`

12. `$ http-server -p 7070`

  http://localhost:7070/ 로 페이지 확인

  인데 나 왜 오류.. 모르겠다..
