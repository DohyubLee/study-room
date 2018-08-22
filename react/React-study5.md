- **AJAX, Promise, async, await ( 코드 설명 )**
```javascript
import React, { Component } from 'react';
import './App.css';
import Movie from './Movie';

class App extends Component {
  state = {}
  
  componentDidMount() {
    this._getMovies();
  }
  _renderMovies = () => {
    const movies = this.state.movies.map(movie => {
      return <Movie title={movie.title} poster={movie.large_cover_image} key={movie.id} />
    })
    return movies;
  }

  _getMovies = async () => {  //async는 비동기함수로 선언한다는 의미
    const movies = await this._callApi(); //await를 함수 호출할때 지정해주면 값이 리턴될때까지 다음 라인으로 넘어가지않는다
    this.setState({
      movies
    })
    // 위에 movies는 최신 자바스크립트 방식
  }
  _callApi = () => {
    return fetch("https://yts.am/api/v2/list_movies.json?sort_by=rating") //AJAX를 구현하는 최신 방법
    .then(res => res.json())  //json()은 데이터를 확인할수있도록 json으로 바꿔줌
    .then(json => json.data.movies)  //문제가 없다면 json.data.movies가 리턴된다, 즉 _getMovies()에서 변수 movies에 이값이 담긴다.
    .catch(err => console.log(err)) //문제가 생기면 여기로
  }
  render() {
    console.log("render()")
    return (
      <div className="App">
        {this.state.movies ? this._renderMovies() : 'Loading'}
      </div>
    );
  }
}

export default App;

```
