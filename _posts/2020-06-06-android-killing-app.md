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

## 안드로이드 앱 완전 종료하기

### 구현중인 동작

  * 카카오톡 채팅방에서 '뒤로가기'를 눌렀을 때, 프로필 화면을 통해서 채팅방에 입장했어도, '채팅리스트' 화면으로 돌아가도록 하는 동작.

### 문제

  * 채팅방에서 메인액티비티로 돌아오는건 성공(Flag 사용). 근데 그 상태에서 다시 '뒤로가기' 버튼을 누르면 앱이 종료되는 것이 아니라 히스토리에 남아있는 동작을 했다.
    * 이번 경우는 종료버튼을 눌렀을 때 ExpandableListView를 확장 했던 히스토리가 반복된 후에 다시 종료버튼을 누르면 종료되는 상황.

### 해결

```java
moveTaskToBack(true); // 현재 앱을 백그라운드로 이동. 
finishAndRemoveTask(); // 액티비티를 종료.
android.os.Process.killProcess(android.os.Process.myPid()); // 프로세스 종료
```

### 추가

  * onBackPressed() 메소드를 통해서 안드로이드 자체의 '뒤로가기' 버튼을 눌렀을 때의 이벤트 처리가 가능하다.
