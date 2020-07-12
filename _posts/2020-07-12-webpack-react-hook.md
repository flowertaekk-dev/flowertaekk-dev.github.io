---
title: "Webpack react hook"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - webpack
  - react hook
  - basics
toc: true
---

## React setting with Webpack

### 1. Download react library

{% highlight cmd  %}
$ npm i --save-dev react react-dom
{% endhighlight  %}

### 2. Download Babel for react

{% highlight cmd  %}
$ npm i --save-dev @babel/preset-react
{% endhighlight  %}

### 3. Edit .babelrc

@babel/preset-react 추가

{% highlight javascript  %}
{
    "presets": [
     "@babel/preset-env",
     "@babel/preset-react"
    ]
}
{% endhighlight  %}

### 4. React 코드추가하고 실행하면 끝.
~                                        
