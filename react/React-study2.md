- 코드 설명
  - App.js //메인 컴포넌트
  ```javascript
  import React, { Component } from 'react';
  import './App.css';
  import Movie from './Movie';

  // const movies = [  
  //   {
  //     title: "마녀",
  //     poster: "https://img.sbs.co.kr/newsnet/etv/upload/2018/06/26/30000605681_1280.jpg"
  //   },
  //   {
  //     title: "원피스",
  //     poster: "http://image.chosun.com/sitedata/image/201412/23/2014122301920_0.jpg"
  //   },
  //   {
  //     title: "헌터헌터",
  //     poster: "http://image.yes24.com/momo/TopCate0001/kepub/X_851470.jpg"
  //   },
  //   {
  //     title: "원펀맨",
  //     poster: "https://laftelimage.blob.core.windows.net/items/thumbs/large/f3203d2d-13e7-43fc-afb0-a43a9a5fe56b.jpg"
  //   }
  // ];    //state로 옮김

  class App extends Component {
    state = {
      greeting : 'Hello!',
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
        }
      ]
    }
    componentDidMount() {
      setTimeout(() => {
        //this.state.greeting = "Hello again!"    //state는 직접 변경 X
        // this.setState({
        //   greeting: "Hello again!"
        // })
        this.setState({
          movies: [
            ...this.state.movies, //이전 데이터 ,없으면 이전 데이터 출력 X
            {
              title: "나루토",
              poster: "http://dh.aks.ac.kr/Edu/wiki/images/2/2e/%EB%82%98%EB%A3%A8%ED%86%A0_%EC%A0%84%EC%B2%B4.PNG"
            }
          ]
        }) //데이터 추가해보기 예제
      },3000)
      //mount완료 후 3초뒤 state값 변경
    }
    render() {
      console.log("render()")
      return (
        <div className="App">
          {this.state.greeting}
          {
            this.state.movies.map((movie, index) => {
              return <Movie title={movie.title} poster={movie.poster} key={index} />
            })
          }
        </div>
      );
    }
  }

  export default App;

  ```
  - Movie.js  //자식 컴포넌트
  ```javascript
  import React, { Component } from 'react';
  import './Movie.css';
  import PropTypes from 'prop-types'; //추가 모듈 props의 타입체크


  class Movie extends Component {

      static propTypes = {
          title: PropTypes.string.isRequired, //isRequired는 상속되었는지 체크
          poster: PropTypes.string //부모로 부터 받은 데이터 poster의 데이터 타입 체크
      }

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

  class MoviePoster extends Component {
      render() {
          return (
              <img src={this.props.poster} />
          )
      }
  }

  export default Movie;
  ```
