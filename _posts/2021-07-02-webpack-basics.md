---
title: "Webpack basics"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - webpack
  - basics
toc: true
---

## Webpack basics

### 설치하기

`npm install webpack webpack-cli`

### Webpack 기초 설정

1. 소스파일이 어디에 있는지 webpack에 설정해줘야 함.
2. 번들링 결과물을 어디에 저장할지 설정해줘야 함.

```js
// webpack.config.js

module.exports = {
  entry: './index.js',
  output: {
    filename: 'bundle.js', // convention
    path: __dirname + '/dist', // absolute path만 가능. 참고: __dirname은 노드 전역변수로 현재 파일위치를 의미!
  },
  //mode: 'production|development'
};

```

### 실행

일반적으로, `package.json` 에 스크립트를 정의해놓고 사용한다.

```js
script: {
  "build": "webpack --mode=production" // full path를 입력하지 않아도, 기본 build path가 node_modules/.bin/
}
```

### Loaders

webpack은 기본적으로 `js` 만 인식한다.
`Loaders` 는 webpack이 `js` 외의 다른 타입의 파일들도 인식할 수 있도록 해준다.

### Plugins

webpack을 확장할 수 있도록 해준다!
webpack은 plugable tool 로 다른 확장프로그램을 추가해서 연동할 수 있다.

### Babel

[Babel official page](babeljs.io)

다양한 브라우저에서 js가 문제없이 동작할 수 있도록 컴파일링 해준다.

webpack과 babel를 별개로 사용할 수도 있지만, 주로 둘을 조합해서 사용함.

### 설치하기

`npm install -D @babel/core @babel/preset-env babel-loader`

`// @babel/preset-<preset name>`

#### Babel Core

js 코드를 컴파일링하는 역할

#### Babel Preset

어떤 버전의 js를 사용할지 설정?
[doc 참고](https://babeljs.io/docs/en/presets)

#### Babel Loader

webpack 과 함께 사용하기 위해서 Loader를 통해서 webpack을 로딩할 수 있다.
