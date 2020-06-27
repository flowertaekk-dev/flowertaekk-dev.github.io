---
title: "Android SideBar"
last_modified_at: 2020-06-07
header:
  overlay_color: "#333"
categories:
  - Development
  - Android
tags:
  - KakaoTalk clone coding
  - Side bar
toc: true
---

Drawer를 이용해서 SideBar구현하기

## 채팅방에서 햄버거 버튼 누르면 사이드 메뉴 열리게 하기

* 네이게이션 참고자료
  * [Navigation 디자인 가이드](https://material.io/design/navigation/understanding-navigation.html)
  * [Google Navigation 공식 가이드](https://developer.android.com/guide/navigation/navigation-ui#java)
  * [DrawerLayout 사용방법 자세히 나와있음](https://recipes4dev.tistory.com/139)
  * [DrawerLayout 만들기](https://erichika.tistory.com/47)

## 구현 방법

1. 메인 레이아웃을 DrawerLayout으로 바꾼다.
2. [layout resource에 drawer용으로 resource를 추가한다](https://github.com/flowertaekk-dev/cloneKakaoTalk/blob/master/app/src/main/res/layout/chatting_room_side_drawer.xml)
3. 메인 레이아웃에 include 해준다.
```xml
<include layout="@layout/chatting_room_side_drawer" />
```

4. Activity에서 기능구현
```java
DrawerLayout.openDrawer(Gravity.RIGHT); // 참고자료 참고
```

## 반성

* 최악의 코드가 생겨난 듯하다.
    * 버튼들을 enum으로 관리하는게 좋은 방법이 아닌걸까
