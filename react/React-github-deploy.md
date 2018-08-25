- **react app github page를 이용하여 배포하기!**
  - 우선 해당 프로젝트에 git이 설정되었는지 확인 안되있으면 `git init` 명령어 실행
  - github에 프로젝트 올리기( push 하기)
  - 빌드하기  터미널에서 `npm run build` 실행
  - 실행 후 터미널을 보면 `"homepage" : "http://myname.github.io/myapp"` 가 있는데 ( `myname`에는 내 github username을 넣고 
  `myapp`에는 프로젝트명(레퍼지토리) ) package.json에 추가/저장 후 다시 빌드한다.
  - 그리고 다시 터미널에서 `package.json` 에 추가하라는 코드를 입력하고 `npm install --save-dev gh-pages` 실행한다
  - 모든게 정상적으로 실행된후 `npm run deploy`를 실행하면 깃헙에 디플로이가됨 설정한 주소로 들어가면 나의 app을 볼수있다.
