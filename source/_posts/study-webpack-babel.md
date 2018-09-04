---
title: 웹팩 + 바벨
date: 2018-09-04 17:00:00
tags:
- webpack
- babel
---
바벨과 웹팩을 간단하게 알아 보았습니다.
바벨을 그냥 사용할 수도 있지만 Browserify, Grunt, Gulp, Rollup과 같은 툴들과 연결해서 사용하곤 합니다.
프로젝트를 웹팩으로 관리하고 웹팩에서 바벨을 사용하도록 설정을 해보겠습니다.

### webpack 설치
``` bash
$ yarn add --dev webpack webpack-cli
```

`webpack.config.js` 파일을 생성합니다.
웹팩은 기본값으로 이 파일의 설정으로 실행합니다. 다른 파일명으로 변경할 수도 있습니다.

### Entry
``` js
module.exports = {
  entry: './src/index.js'
};
```
`entry`는 번들링의 기준이 되는 시작되는 파일을 지정합니다. 멀티로 지정할 수도 있습니다.
기본 값은 `./src/index.js` 입니다.


### Output
``` js
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'main.js'
  }
};
```
`output`는 번들링의 결과로 파일명과 위치를 지정합니다.
기본 값은 `./dist/main.js` 입니다.

### babel 설치
babel으로만 사용할 때에는 `@babel/cli`를 사용하였지만 webpack에서 사용할 수 있게 연결해주는 역활은 `babel-loader`가 합니다.
``` bash
$ yarn add --dev @babel/core @babel/preset-env babel-loader
```
- `@babel/cli` 대신 `babel-loader`를 설치합니다.


``` js
const path = require('path');

module.exports = {
  entry: './src/index.js',
  output: {
    path: path.resolve(__dirname, 'dist'),
    filename: 'main.js'
  },
  module: {
    rules: [
      {
        test: /\.js$/,
        exclude: /node_modules/,
        use: {
          loader: 'babel-loader',
          options: {
            presets: ['@babel/preset-env']
          }
        }
      }
    ]
  }
};
```
- `module` 속성에 `xxx-loader`등의 로더설정을 넣습니다.
- `.js` 확장자 파일을 설정해서 특정 확장자 파일이 로더 실행을 거치도록 합니다.

#### 참고
- [Using Babel](https://babeljs.io/en/setup#installation)
- [webpack - Concepts](https://webpack.js.org/concepts/)
- [babel-loader](https://webpack.js.org/loaders/babel-loader/)
