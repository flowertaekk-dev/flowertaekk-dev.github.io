---
title: "HTML tag"
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

HTML basics

## 박스 모델

* box는 사용자에게 보여지지 않는다.
* item은 사용자에게 보여진다.

* HTML markup을 진행할 때는 header, nav, main, aside, footer 등을 사용한다.
    * div로 박스모델 만들지 말기.

* main > section > article
    * article은 반복되서 사용되는 컴포넌트들을 모아주는 박스

* div는 묶어서 스타일링할 필요가 있을 때 사용

### Box and Item tag

| Box | Item |
| --- | ---- |
| header  | a  |
| footer  | button  |
| nav | input  |
| aside  | label  |
| main  | image |
| section  | video  |
| article  | audio  |
| div  | map  |
| span  | canvas  |
| form  | table  |

## Block & Inline

* Block level tag는 한 줄을 통째로 차지한다.
* Inline level tag는 공간이 허용하면 다른 tag옆에 배치가 가능하다.

## Tips for tag usage

* input 태그는 보통 label tag와 함께 자주 쓰인다.
```html
<lable for="">Name: </label>
<input type="text" />
``` 

## 참고자료

* [드림코딩 by 엘리](https://www.youtube.com/watch?v=OoA70D2TE0A)
~                                                                  
