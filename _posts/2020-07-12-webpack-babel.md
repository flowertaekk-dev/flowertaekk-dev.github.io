---
title: "Webpack babel"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - webpack
  - babel
  - basics
toc: true
---

## babel 설정하기

### 1. babel 다운로드

{% highlight cmd  %}
$ npm i --save-dev @babel/core babel-loader @babel/preset-env
{% endhighlight  %}

### 2. babel 설정파일 생성

* .babelrc는 프로젝트 루트에 설정하고, babel의 동작하는 룰을 설정하는 파일이다.
* json 타입으로 설정

{% highlight cmd  %}
{
 "presets": [
  "@babel/preset-env"
 ]
}
{% endhighlight  %}

### 참고

[참고사이트](https://medium.com/@shlee1353/%EC%9B%B9%ED%8C%A9-%EC%9E%85%EB%AC%B8-3-webpack-4-babel7-%EC%84%A4%EC%A0%95-%EB%B0%8F-%EC%9B%B9%EC%84%B1%EB%8A%A5-%EC%B5%9C%EC%A0%81%ED%99%94-4d5162a69a71)
