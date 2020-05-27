---
title: "Usage of attr in Android"
last_modified_at: 2020-05-27
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
  - Android
tags:
  - KakaoTalk clone coding
  - attr 속성
toc: true
---

## 안드로이드 프로젝트에서 ?attr/ 의 사용법

### 문제

  * 특정 layout을 클릭했을 때, 버튼이 클릭되었을 때와 동일한 효과(effect)를 주고 싶었다.

### 해결

  * 다음의 코드를 layout 선언부에 추가했다.
```xml
android:background="?attr/selectableItemBackground"
```

### 궁금증

  * ?attr 이 뭐지?
  * ?attr을 이용해서 Android에서 기본으로 제공하는 속성들을 사용할 수 있다.
    * ~/.gradle/caches/생략/res/values/values.xml 에 다양한 속성들이 설정되어 있다.
    * [document](https://developer.android.com/reference/android/R.attr?hl=ko)
    * [스타일 속성](https://developer.android.com/guide/topics/ui/themes?hl=ko#Properties)

### 추가 발견

  * ?attr/actionBarSize 같은 크기 설정도 있었다.
