---
title: Babel 기초
date: 2018-08-30 17:57:18
tags:
- Babel
- 바벨
---

바벨은 자바스크립트 컴파일러(compiler)입니다. ECMAScript 2015+ 이상의 코드를 지금의 브라우저 또는 오래된 브라우저 또는 다른 환경(Node.js)에 맞도록 변환합니다.

프로젝트에 `@babel/core`, `@babel/cli`, `@babel/preset-env`를 설치합니다.
``` bash
$ yarn add --dev @babel/core @babel/cli @babel/preset-env
```
- 버전7 이후로 바벨괸련 모듈은 '@babel/모듈이름' 으로 나타냅니다.
- 버전7 이후로 바벨은 `@babel/core`, `@babel/cli` 두 개로 분리됩니다.
- `@babel/core`: 코어 모듈
- `@babel/cli`: CLI(command line interface)로 바벨을 실행시킬 수 있습니다. 바벨을 webpack이나 Gulp에서 사용한다면 필요가 없습니다.
- `@babel/preset-env`: target environment를 지정해서 코드를 변환합니다.

`package.json` 파일에서 설치를 확인할 수 있습니다.
``` json
  "devDependencies": {
    "@babel/cli": "^7.0.0",
    "@babel/core": "^7.0.0",
    "@babel/preset-env": "^7.0.0"
  },
```

`.babelrc` 바벨에서 사용할 preset 설정 파일을 작성합니다.
``` rc
{
  "presets": ["@babel/preset-env"]
}
```

`src/main.js` ES6문법을 사용한 파일로 타켓 파일을 만듭니다.
``` js
[1, 2, 3].map((n) => n + 1);
```

`package.json` 파일에 바벨 실행을 위한 스크립트를 추가합니다.
``` json
  "scripts": {
    "transform": "babel src/main.js --out-file dist/compile.js"
  }
```

바벨 실행
``` bash
$ yarn run transform
```

`dist/compile.js` 변환된 파일을 확인 할 수 있습니다.
``` js
"use strict";

[1, 2, 3].map(function (n) {
  return n + 1;
});
```

#### 참고
[What is Babel?](https://babeljs.io/docs/en)
[Usage Guide](https://babeljs.io/docs/en/usage)
