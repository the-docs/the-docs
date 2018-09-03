---
title: webpack 기초
date: 2018-09-02 15:44:33
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

### npm 확인
``` bash
$ npm -v
6.2.0
```

### yarn 확인
``` bash
$ yarn -v
1.9.4
```

#### 참고
- [webpack - Getting Started](https://webpack.js.org/guides/getting-started/)
