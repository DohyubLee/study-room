- **state없는 컴포넌트( 함수형 컴포넌트 )**
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
// 일반적인 컴포넌트
// class MoviePoster extends Component {
//     static propTypes = {
//         poster: PropTypes.string.isRequired
//     }
//     render() {
//         return (
//             <img src={this.props.poster} alt="Movie Poster" />
//         )
//     }
// }

//state가 없는 컴포넌트, lifecycle도 없음, props는 사용가능
function MoviePoster({poster}) {
    return (
        <img src={poster} alt="Movie Poster" />
        // class가 아닌기 떄문에 this라는 키워드 사용 안함
        // 위에 처럼 props를 사용함
    )
}
//state가 없는 컴포넌트에서 prototypet 사용법
MoviePoster.prototype = {
    poster: PropTypes.string.isRequired
}

export default Movie;
```
