- App.js
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
      return <Movie title={movie.title_english} poster={movie.medium_cover_image} genres={movie.genres} synopsis={movie.synopsis} key={movie.id} />
      // css로 꾸미기에 앞서 필요한 데이터 모두 movie컴포넌트로 props하기
    })
    return movies;
  }

  _getMovies = async () => {
    const movies = await this._callApi();
    this.setState({
      movies
    })
  }
  _callApi = () => {
    return fetch("https://yts.am/api/v2/list_movies.json?sort_by=rating")
    .then(res => res.json())
    .then(json => json.data.movies)
    .catch(err => console.log(err))
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

- Movie.js css로 꾸미기전 클래스네임 및 컴포넌트 분할
```javascript
import React, { Component } from 'react';
import './Movie.css';
import PropTypes from 'prop-types'; //추가 모듈 props의 타입체크


class Movie extends Component {

    static propTypes = {
        title: PropTypes.string.isRequired,
        poster: PropTypes.string,
        genres: PropTypes.array.isRequired,
        synopsis: PropTypes.string.isRequired

    }

    render() {
        console.log(this.props);
        return (
            <div className="Movie">
                <div className="Movie__Columns">
                    <MoviePoster poster={this.props.poster} alt={this.props.title} />
                </div>
                <div className="Movie__Columns">
                    <h1>{this.props.title}</h1>
                    <div className="Movie__Genres">
                        {this.props.genres.map((genre, index) => <MovieGenre genre={genre} key={index} />)}
                    </div>
                    <p className="Movie__Synopsis">
                        {this.props.synopsis}
                    </p>
                </div>
            </div>
        );
    }
}
// MoviePoster, MovieGenre 추가 컴포넌트 생성
function MoviePoster({poster, alt}) {
    return (
        <img src={poster} alt={alt} title={alt} className="Movie__Poster" />
    )
}
function MovieGenre({genre}) {
    return (
        <span className="Movie__Genre">{genre}</span>
    )
}
MoviePoster.prototype = {
    poster: PropTypes.string.isRequired,
    alt: PropTypes.string.isRequired
}
MovieGenre.prototype = {
    genre: PropTypes.string.isRequired
}

export default Movie;
```
