---
title: "CSS basics"
last_modified_at: 2020-07-04
header:
  overlay_color: "#333"
categories:
  - Development
  - HTML
tags:
  - HTML
  - basics

toc: true
---

CSS basics

## 의미, 정의

* Cascading Style Sheet : CSS
    * Cascading이란? 폭포!
        * 페이지가 rendering될 때 관련된 Style sheet이 있는지 위에서 아래로 하나하나 찾아간다.
            * Author style(우리가 작성한 style sheet) -> User Style(사용자가 지정) -> Browser default style sheet

* CSS의 폭포 구조를 끊어먹는 property: !important
    * 좋지 않은 아키텍쳐를 사용하고 있다는 의미
    * 최대한 쓰지 않는게 좋다.

## 선택자

| Selectors |  |
| --------- |  |
| Universal  | *  |
| Type  | Tag ex) div  |
| ID  | #id  |
| Class  | .class  |
| State  | : ex) div:hover |
| Attribute  | [ ] |

### Selector 연습

[Selector 연습](https://flukeout.github.io/)

### CSS 기본 문법

```css
selector {
  property: value;
}
```

### Attribute Tips!

* a 태그중에 href 속성을 가지고 있는 애들만 대상

```css
a[href] {}
```

* a 태그중에 href 속성을 가지고 있고, 속성값이 naver로 시작하는 애들만 대상

```css
a[href^="naver"] {}
```

* a 태그중에 href 속성을 가지고 있고, 속성값이 .com으로 끝나는 애들만 대상

```css
a[href$=".com"] {}
```

## 스타일링

### justify-content

* 중심축에서 아이템들을 어떻게 배치할 것인지 결정.
  * flex-start: default
  * flex-end: *아이템들의 순서는 유지하되*, row가 main axis인 경우에는 오른쪽 정렬되고, column이 main axis인 경우에는 아래 정렬이 된다.
  * center: 중앙정렬
  * space-around: 아이템 주변에 공백을 넣어준다.
  * space-evenly
  * space-between

### align-items

* 반대축에서 아이템들을 어떻게 배치할 것인지 결정.
  * 대부분 justify-content의 속성값들과 유사한 듯.
  * baseline: 크기가 다른 아이템들이 있어도 text를 기준으로 라인이 정렬될 수 있도록 한다.

### align-content


* 반대축에서 아이템들을 어떻게 배치할 것인지 결정.
  * align-items와의 차이점은?
  * justify-content과 동일한 속성값

### order

* 아이템의 순서 지정
  * 잘 안 쓰인다.

## 헷갈리는 컨셉

### display

* display: block;
  * 내용물이 없어도 크기조절이 가능하다. (width 등)
* display: inline;
  * 내용물이 없으면 width를 설정해도 보이지 않는다.
  * 내용물의 크기에 따라 변한다.
* display: inline-block;
  * inline으로 한 줄에 여러 Tag요소가 나열되지만, block 성질도 갖고 있어서 내용물이 없어도 크기설정이 가능하다.

### height: 100% vs. 100vh (viewport height?)

* 100%는 부모 tag를 100% 채우겠다는 것.
  * Default로 html도 브라우저를 100% 채우고 있지 않다.
* 100vh는 현재 보이는 viewport height의 100%를 다 쓰겠다는 의미.

### position

* 기본값은 position: static;
  * brower의 기본값을 이용한다는 의미
* position: relative;
  * 원래 있어야할 장소에서 이동이 이루어진다. (left, top..)
* position: absolute;
  * 가장 가까이에 있는 컨테이너로부터 이동이 이루어진다.
* position: fixed;
  * 현재 사용중인 윈도우 자체로부터 계산해서 이동 됨.
* position: sticky;
  * 원래 있어야할 장소에서 스크롤링이 일어나도 사라지지않고 화면에 유지된다.

### float

* Image나 text을 레이아웃하기 위한 속성
  * left, center, right

## CSS의 꽃 FlexBox

* FlexBox란?
  * 박스의 크기를 화면의 크기에 따라 자유롭게 변경가능한 컴포넌트(?)
  * 박스의 레이아웃을 유연하게 설정가능하도록 도와주는 컴포넌트(?)

### point

* FlexBox는 박스에 지정하는 속성값들이 있고, 박스 안에 들어가는 Item들에 지정하는 속성값들이 있다.
* FlexBox에는 중심축(main axis)와 반대축(cross axis)가 있다.
  * 우리가 지정할 수 있다!

### How to use?

1. display:flex; 추가하기
2. flex-direction property 추가 (main axis를 설정)
  * row
  * row-reverse
  * column
  * column-reverse
3. flex-wrap
  * nowrap: default, 화면이 작아져도 아이템들이 한줄에 유지된다. (크기만 작아짐)
  * wrap: 아이템들이 한 줄에 가득차면 자동으로 다음 라인으로 이동.
  * wrap-reverse
4. flex-flow
  * flex-direction과 flex-wrap설정을 한 번에한다. ex) flex-flow: row nowrap
5. flex-grow (item에 설정)
  * 화면을 가득 채울 수 있도록 늘어난다.
  * ex) flex-grow: 1
6. flex-shrink (item에 설정)
  * 컨테이너가 작아졌을 때 어떻게 행동하는지를 결정
  * ex) flex-shrink: 2 -> 화면이 작아질 때 다른 아이템보다 두배 더 줄어든다. 
7. flex-basis (item에 설정)
  * 아이템들이 공간을 얼마나 차지해야하는지 세부적으로 명시할 수 있게 도와주는 property
  * ex) flex-basis: 30%
8. align-self (item에 설정)
  * 아이템별로 아이템들을 정렬할 수 있다.
  * 컨테이너에 지정된 것을 벗어나서 아이템을 개별적으로 배치하고 싶을 때 사용한다.

### FlexBox 연습

[FLEXBOX FROGGY](https://flexboxfroggy.com/)

### 참고자료

[CSS FlexBox](https://www.youtube.com/watch?v=7neASrWEFEM)
