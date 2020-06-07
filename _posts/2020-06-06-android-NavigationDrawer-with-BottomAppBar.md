---
title: "Killing Android App completely"
last_modified_at: 2020-06-06
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
  - Android
tags:
  - KakaoTalk clone coding
toc: true
---

## Navigation Drawer를 아래에서 위로 나오도록 구현하기

### 구현 동작

  * 카카오톡 채팅입력란 왼쪽에 있는 버튼을 누르면 아래에서 위쪽으로 Drawer메뉴가 나오도록 한다.

### 문제

  * 기본으로 제공되는 NavigationDrawer는 사이드바 기능만을 제공하는 듯하다.

### 해결

  * BottomAppBar를 사용해서 그 안에 NavigationDrawer를 구현하는 방법이 있었다.

### BottomAppBar 사용해서 NavigationDrawer 구현하는 방법

  1. gradle에 모듈 추가
```gradle
implementation 'com.google.android.material:material:1.0.0-alpha1'
```
  2. 최상단 Layout(여기에서는 채팅방layout)에 style추가
```xml
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@color/colorChattingDefault"
    tools:context=".ChattingRoomActivity"
    style="@style/Widget.MaterialComponents.BottomAppBar">
```
  3. 화면 아래에 CoordinatorLayout 추가하고, 그 안에 BottomAppBar 추가
    * BottomAppBar는 CoordinatorLayout안에서만 작성할 수 있다는 경고가 떠서 어쩔수 없이 CoordinatorLayout사용.
```xml
    <androidx.coordinatorlayout.widget.CoordinatorLayout
        android:id="@+id/chatting_room_footer_container"
        android:layout_width="match_parent"
        android:layout_height="?attr/actionBarSize"
        android:background="@color/colorWhite"
        android:layout_alignParentBottom="true">

        <com.google.android.material.bottomappbar.BottomAppBar
            android:id="@+id/chatting_room_footer"
            style="@style/Widget.MaterialComponents.BottomAppBar"
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:layout_gravity="bottom"
            app:navigationIcon="@drawable/ic_add_circle" <!-- Drawer button 이미지 -->
            />

    </androidx.coordinatorlayout.widget.CoordinatorLayout>
```
  4. res/menu에 리소스 추가
```xml
<?xml version="1.0" encoding="utf-8"?>
<menu xmlns:android="http://schemas.android.com/apk/res/android">
    <!-- 메뉴 -->
</menu>
```
  5. Blank Fragment생성
  6. [상속을 Fragment가 아니라 BottomSheetDialogFragment를 상속하도록 변경](https://github.com/flowertaekk-dev/cloneKakaoTalk)
  7. [새로 생성된 Fragment layout에 NavigationView추가](https://github.com/flowertaekk-dev/cloneKakaoTalk)
```xml
<com.google.android.material.navigation.NavigationView
        android:id="@+id/chatting_bottom_drawer_menu"
        android:layout_width="match_parent"
        android:layout_height="match_parent"
        app:menu="@menu/chatting_bottom_drawer_menu"/>
```
  8. 추가한 NavigationView에 menu지정
```xml
app:menu="@menu/chatting_bottom_drawer_menu"
```
  9. [추가한 Blank Fragment에 NavigationItemSelectedListener 구현](https://github.com/flowertaekk-dev/cloneKakaoTalk)
  10. [Activity에서 BottomAppBar onClickListener 구현](https://github.com/flowertaekk-dev/cloneKakaoTalk)
```java
        BottomAppBar bottomAppBar = findViewById(R.id.chatting_room_footer);
        bottomAppBar.setNavigationOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                ChattingBottomDrawerMenu chattingBottomDrawerMenu = new ChattingBottomDrawerMenu();
                chattingBottomDrawerMenu.show(getSupportFragmentManager(), "TAG");
            }
        });
```

### 추가 문제

  * 이건 아이템이 세로로 정렬이 되고, '채팅 입력칸'이 없어진다는 점에서 이대로는 실패다.
  * 다른 방법은?
