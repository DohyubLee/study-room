## 커링 함수
===============
- 커링 개념, 구조
  - 특정 함수에서 정의된 인자의 일부를 넣어 고정시키고, 나머지를 인자로 받는 새로운 함수를 반환하는 함수
```
function add(a) {
  return function(b) {
    return a + b; 
  }
}
```
또는
```
let add = a => b => {
  return a + b;
}
```
예) add(1) 이 실행이되면 처음 전달된 인자 1을 가지고 있는 익명함수가 리턴된다.
```
function(b) {
  return 1 + b;
}
```
