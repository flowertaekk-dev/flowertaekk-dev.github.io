---
title: "Webpack typescript"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - webpack
  - typescript
  - basics
toc: true
---

## Webpack setting for TypeScript

### 1. Download typescript and awesome-typescript-loader

### 2. Webpack config 파일에 entry 추가하기

{% highlight javascript  %}
    entry: {
        main: ["./src/main.js"],
        ts: ["./src/index.ts"]
    },
{% endhighlight %}

### 3. src/index.ts 생성하기

### 4. Webpack config 파일에 module's rule 추가하기

{% highlight javascript  %}
            {
                test: /\.ts$/,
                use: [
                    {
                        loader: 'awesome-typescript-loader'
                    }
                ],
                exclude: /node_modules/
            },
{% endhighlight %}

### 5. tsconfig.json 파일만들기

tsconfig.json는 ts를 컴파일하기 위한 룰을 설정하는 곳.

{% highlight javascript  %}
{
    "compilerOptions": {
        "module": "commonjs",
        "moduleResolution": "node",
        "target": "es5",
        "allowJs": true,
        "lib": ["es5", "es6", "dom"],
        "sourceMap": true,
        "experimentalDecorators": true,
        "emitDecoratorMetadata": true
    }
}
{% endhighlight %}


## Setting TypeScript with React

### 1. Create with create-react-app

### 2. Install packages

{% highlight javascript  %}
npm i --save-dev typescript @types/node @types/react @types/react-dom
{% endhighlight %}

### 3. App.js를 App.tsx 파일로 변경
 
