---
title: "Mobx"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - react 
  - mobx
toc: true
---

## Mobx

### Package 추가

{% highlight javascript %}
$ npm i --save mobx mobx-react
{% endhighlight  %}

### Decorator

#### 1. `@observable`

* React의 state와 비슷한 역할.
* MobX 상에서 변수와 같은 역할을 하고, Store에 넣고 관리하고 싶은 변수는 `@observable` 키워드로 선언한다.

{% highlight javascript %}
@observable valueToBeStored:string = "hello"
{% endhighlight  %}

#### 2. `@action`

* React의 setState와 비슷한 역할.

{% highlight javascript %}
@action changeStoreValue = (value: string) => {
        this.myStore = value;
}
{% endhighlight  %}

### 설정

#### 1. 최상단 컴포넌트에서 Provider를 설정

{% highlight javascript %}

import { Provider } from 'mobx-react'
import MyStore from './MyStore'

const myStore = new MyStore()

const RenderComponent = () => {
	<Provider myStore={myStore}>
		<App />
	</Provider>
}

{% endhighlight  %}

#### 2. MobX를 사용할 곳에서 세팅

{% highlight javascript %}
import { observer, inject } from 'mobx-react'

@inject("store-name") // Store에 있는 변수 호출
@observer // Store 값을 관찰하고 변화가 있으면 rerendering하겠다는 의미
export default class App extends Reaxt.Component<any> {
	render() {
		return <h1>{this.props.<store-name>}</h1>
	}
}
{% endhighlight  %}
