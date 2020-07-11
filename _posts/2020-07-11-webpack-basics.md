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

Webpack이란?

* 자바스크립트로 만들어진 Static Module Bundler이다.
* JavaScript, Style sheet, image등 모든 것을 자바스크립트 모듈로 로딩해서 사용한다.
* 웹팩의 주요 네 가지 개념으로 *Entry*, *Output*, *Loader*, *Plugin* 가 있다.

## 기본 설정

### src, dist, config 폴더 만들기

왜 만들어야하는지는 잘 모르겠다. 꼭 필요한건가?

### npm 초기화하기

{% highlight javascript  %}
$ npm init -y
{% endhighlight %}

### Download webpack

{% highlight javascript  %}
$ npm install -g webpack webpack-cli
{% endhighlight %}

### config 파일 생성하기

{% highlight javascript  %}
config/webpack.dev.js
{% endhighlight %}

## Dev-server 설정해보기

###  webpack.dev.js 에 설정

{% highlight javascript  %}
const path = require('path')

module.exports = {
    entry: {
        main: "./src/main.js" 
    },
    mode: "development",
    output: {
        filename: "[name]-bundle.js", // in this case, it will be main-bundle.js
        path: path.join(__dirname, '../dist'),
        publicPath: '/'
    },
    devServer: {
        contentBase: "dist",
        watchContentBase: true
    }
}

{% endhighlight %}

### webpack 실행하기: main-bundle.js 생성

{% highlight javascript %}
$ webpac --config config/webpack.dev.js
{% endhighlight %}

### dist/index.html 에서 main-bundle.js 참조하기

{% highlight javascript %}
<script src="main-bundle.js"></script>
{% endhighlight %}

### webpack-dev-server 다운받기

{% highlight cmd %}
$ npm install --save-dev webpack webpack-cli webpack-dev-server
// 여기서 왜 webpack webpack-cli 도 같이 받는지는 아직 잘 모르겠다.
{% endhighlight %}

### package.js script 수정하기

{% highlight javascript %}
  "scripts": {
    "dev": "webpack-dev-server --config config/webpack.dev.js"
  },
$ webpack --config config/webpack.dev.js // config file path
{% endhighlight %}

### 실행!

{% highlight cmd %}
$ npm run dev
{% endhighlight %}

