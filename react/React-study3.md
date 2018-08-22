- 로딩중 구현해보기( 코드 예시 )
```javascript
import React, { Component } from 'react';
import './App.css';
import Movie from './Movie';

class App extends Component {
  state = {
  }
  
  componentDidMount() {
    setTimeout(() => {
      this.setState({
        movies: [
          {
            title: "마녀",
            poster: "https://img.sbs.co.kr/newsnet/etv/upload/2018/06/26/30000605681_1280.jpg"
          },
          {
            title: "원피스",
            poster: "http://image.chosun.com/sitedata/image/201412/23/2014122301920_0.jpg"
          },
          {
            title: "헌터헌터",
            poster: "http://image.yes24.com/momo/TopCate0001/kepub/X_851470.jpg"
          },
          {
            title: "원펀맨",
            poster: "https://laftelimage.blob.core.windows.net/items/thumbs/large/f3203d2d-13e7-43fc-afb0-a43a9a5fe56b.jpg"
          },
          {
            title: "나루토",
            poster: "http://dh.aks.ac.kr/Edu/wiki/images/2/2e/%EB%82%98%EB%A3%A8%ED%86%A0_%EC%A0%84%EC%B2%B4.PNG"
          }
        ]
      }) //데이터 추가해보기 예제
    },3000)
    //mount완료 후 3초뒤 state값 변경
  }
  //로딩중을 보여주기 위한 예제 코드
  //1. componentDidMount()에서 3초 시간이 흐른 후에 state에 데이터 set
  //2. state는 데이터가 업데이트되면 render()를 실행하도록 되어있음
  //3. 미리 설정되어있는 삼항 연산자에 의해서 _renderMovies()함수 실행
  //4. 화면에선 맨처음 Loading이라는 문자가 출력되고 3초후 movie 데이터가 나오게됨
  _renderMovies = () => {
    const movies = this.state.movies.map((movie, index) => {
      return <Movie title={movie.title} poster={movie.poster} key={index} />
    })
    return movies;
  }
  render() {
    console.log("render()")
    return (
      <div className="App">
        {this.state.movies ? this._renderMovies() : 'Loading'}
        {/* this.state.movies에 데이터 존재 유무에 따라 실행하도록 설정 */}
      </div>
    );
  }
}

export default App;

```
