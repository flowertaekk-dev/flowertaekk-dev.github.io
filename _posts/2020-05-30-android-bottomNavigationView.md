---
title: "Create Footer with BottomNavigationView"
last_modified_at: 2020-05-30
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
  - Android
tags:
  - KakaoTalk clone coding
  - BottomNavigationView
toc: true
---

## BottomNavigationView를 이용해서 Footer만들기

### 문제

  * Activity로 화면을 구성하면서 모든 Activity가 하나의 Footer를 공유하도록 하고 싶었다.
    * 뭔가 효율적이지 못하면서 DRY원칙을 유지하기가 까다롭다는걸 느낌.
  * 이런저런 시도를 하다가 BottomNavigationView를 이용해서 Footer를 만들고 Footer의 메뉴가 클릭되면 Fragment를 이용해서 화면을 구성한다.

### 해결

  1. gradle에 implements문 추가
```gradle
implementation 'com.android.support:design:28.0.0'
```
  2. [Footer 리소스 구현](https://github.com/flowertaekk-dev/cloneKakaoTalk)
  3. [Main 레이아웃 XML에 FrameLayout 추가](https://github.com/flowertaekk-dev/cloneKakaoTalk)
  4. [Main 레이아웃 XML에 BottomNavigationView 추가](https://github.com/flowertaekk-dev/cloneKakaoTalk)
  5. [Fragment 리소스 작성](https://github.com/flowertaekk-dev/cloneKakaoTalk)
  6. [Fragment 클래스 작성](https://github.com/flowertaekk-dev/cloneKakaoTalk)
  7. [MainActivity에 초기화면 설정과 Footer 클릭에 따라서 Fragment 교체가 이루어질 수 있도록 구현](https://github.com/flowertaekk-dev/cloneKakaoTalk)

### 추가 작업

  * 특정 BottomNavigationView item이 선택된 상태라도, 아이콘의 위치가 변하지 않도록 BottomNavigationView에 설정 추가. (선택된 아이템의 아이콘이 위로 조금씩 올라가도록 표현되는 효과를 제거)
```xml
pp:labelVisibilityMode="unlabeled"
```
  * 선택된 item의 아이콘의 색상이 바뀌는 효과는 없애기 위해 MainActivity에 설정 추가.
```java
bottomNavigationView.setItemIconTintList(null);
```

### 생각

  1. 그럼 Activity보다 Fragment만을 사용해서 앱을 구성하는 경우가 더 많겠는데?
