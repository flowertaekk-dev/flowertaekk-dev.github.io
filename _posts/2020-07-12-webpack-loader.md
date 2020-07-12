---
title: "Webpack loader"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - webpack
  - loader 
  - basics
toc: true
---

## Webpack loader setting

CSS loader를 예로 들어 기록한다.

### 1. style-loader css-loader 다운로드

{% highlight css  %}
$ npm i style-loader css-loadeer
{% endhighlight  %}

### 2. css 파일 생성 (src/main.css)

### 3. webpack.dev.js 에 loader 설정

{% highlight css  %}
module: {
        rules: [
            {
                test: /\.css$/,
                use: [
                    {
                        loader: "style-loader"
                    },
                    {
                        loader: "css-loader"
                    }
                ]
            }
        ]
    }
{% endhighlight  %}

## Tips

* devServer 에 `overlay: true` 를 추가해주면 컴파일 에러 등을 화면에 띄어준다.
