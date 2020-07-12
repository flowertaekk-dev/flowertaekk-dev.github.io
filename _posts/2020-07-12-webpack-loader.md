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
* html loader
    * html-loader
    * extract-loader
    * file-loader

### src 디렉토리의 리소스를 webpack을 이용해서 로딩하는 법

#### 1. webpack config 파일에 관련 설정 추가

{% highlight css  %}
             {
                test: /\.html/,
                use: [
                    {
                        loader: "html-loader",
                        options: {
                            attributes: {
                                list: [
                                    {
                                        tag: "img",
                                        attribute: 'src',
                                        type: "src"
                                    }
                                ]
                            }
                        }
                    },
                    {
                        loader: "extract-loader"
                    },
                    {
                        loader: "file-loader",
                        options: {
                            name: "[name].html"
                        }
                    },
                ]
            },
            {
                test: /\.(jpg|gif|png)/,
                use: [
                    {
                        loader: 'file-loader',
                        options: {
                            name: "images/[name].[ext]"
                        }
                    }
                ]
            }
{% endhighlight  %}

#### 2. src/main.js 에서 require문 추가

{% highlight css  %}
require('./resource-path')
{% endhighlight  %}


