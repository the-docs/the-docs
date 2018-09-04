---
title: webpack 기초
date: 2018-09-03 17:44:33
tags:
- webpack
- 웹팩
---

웹팩은 스크립트, 이미지, 스타일, 애셋 파일들을 번들링 합니다.
웹 프로젝트의 규모가 커지고, 복잡성이 증가함에 따라 프로젝트 전체 코드의 양이 증가합니다.
증가한 코드는 한 개의 파일보다는 여러 개의 파일들로 나누면 개발, 관리가 편리합니다.
하지만 분리된 파일들을 하나씩 .html 파일에서 로드하기 보다는 적적한 묶음 형태로 제공하면 사용자는 편리하게 이용가능 합니다.
또한 웹팩은 스크립트 코드 뿐만 아니라 스타일 코드, 이미지 등 파일들의 복잡한 의존성을 관리하는데 편리합니다.

### `webpack`, `webpack-cli`를 설치합니다.
``` bash
$ yarn add --dev webpack webpack-cli
```
- 버전4 이후로 바벨은 `webpack`, `webpack-cli` 두 개로 분리됩니다.
`webpack`: 웹팩 코어 모듈
`webpack-cli`: 웹팩 CLI(command line interface)를 실행하기 위한 모듈

`package.json`파일에서 설치를 확인합니다.
``` json
  "devDependencies": {
    "webpack": "^4.17.2",
    "webpack-cli": "^3.1.0"
  }
```

`lodash`를 설치해서 모듈을 연결해보도록 하겠습니다.
``` bash
$ yarn add lodash
```

`src/index.js`을 작성합니다.
``` js
import _ from 'lodash';

function component() {
  let element = document.createElement('div');

  element.innerHTML = _.join(['Hello', 'webpack'], ' ');

  return element;
}

document.body.appendChild(component());
```
웹에서는 다음과 같은 모듈 방식을 사용할 수 있습니다.
- ES2015 `import`
- CommonJS `require()`
- AMD `define`, `require`
- CSS `@import`
- stylesheet `url(...)`
- html `<img src=...>`

`package.json`파일에 스크립트를 추가합니다.
``` json
  "scripts": {
    "build": "webpack"
  },
```

웹팩 실행
``` bash
$ yarn run build
```
실행 후 `dist/main.js` 파일이 생겼습니다.
`lodash` + `src/index.js` = `dist/main.js`
웹팩에 대한 설정 파일을 만들 수 있지만 지금은 기본 설정으로 실행해 보았습니다.

`dist/index.html`을 작성합니다.
``` html
<!doctype html>
<html>
  <head>
    <title>Getting Started</title>
  </head>
  <body>
    <script src="main.js"></script>
  </body>
</html>
```
웹팩이 생성한 `main.js`파일을 확인해 볼 수 있습니다.

#### 참고
- [webpack - Getting Started](https://webpack.js.org/guides/getting-started/)
