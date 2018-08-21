React 공부
==========
- React 프로젝트 생성하기
  - create-react-app이라는것을 설치( `npm install -g create-react-app` )
  - 터미널창에서 `create-react-app 앱이름`으로 실행하면 앱이 생성
  - `create-react-app` CLI를 사용하여 앱을 생성하면 webpack/babel 등의 React 작업환경을 설정하는 시간을 줄일수있다
  - 개발서버 실행은 `npm start`
- **React는 component에 기반한다.**
- React 앱 기본 구조
  - node_modules
  - public
    - favicon.ico
    - index.html
    - manifest.json
  - src
    - App.css
    - App.js    //메인 컴포넌트, 필요에따라 컴포넌트를 추가생성해서 사용한다
    - App.test.js
    - index.css
    - index.js
    - registerServiceWorker.js
  - package-lock.json
  - package.json 
- 컴포넌트 예시
```
import React, { Component } from 'react';  // 필수적으로 import 해야함
import './App.css';            //따로 모아놓은 css파일을 import 

class App extends Component {  //Component를 상속
  render() {                   //컴포넌트에는 꼭 render()가 있어야함
    return (                   //render()에서 꼭 JSX를 return 해주어야함
      <div className="App">    //이 html같은 코드는 JSX라고 함
        <h1>Hello React</h1>
      </div>
    );
  }
}

export default App;
```
- 컴포넌트 추가해보기
```
import React, { Component } from 'react';
import './Movie.css';

class Movie extends Component {
    render() {
        console.log(this.props);
        return (
            <div>
                <MoviePoster poster={this.props.poster} />
                <h1>{this.props.title}</h1>
            </div>
        );
    }
}
export default Movie;
```
```
import React, { Component } from 'react';  // 필수적으로 import 해야함
import './App.css';            //따로 모아놓은 css파일을 import 

class App extends Component {  //Component를 상속
  render() {                   //컴포넌트에는 꼭 render()가 있어야함
    return (                   //render()에서 꼭 JSX를 return 해주어야함
      <div className="App">    //이 html같은 코드는 JSX라고 함
        <h1>Hello React</h1>
      </div>
    );
  }
}

export default App;
```
