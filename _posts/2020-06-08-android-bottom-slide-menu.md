---
title: "Android Bottom Menu"
last_modified_at: 2020-06-08
header:
  overlay_color: "#333"
categories:
  - Development
  - Android
tags:
  - KakaoTalk clone coding
  - Bottom slide menu
toc: true
---

Android Bottom menu만들기 (카카오톡 이모티콘 메뉴와 동일)

## 관련 라이브러리가 있을까 해서 이것저것 찾아봤는데 실패만해서, 직접 만든다.

### 구현동작

  * 채팅창 옆에 있는 플러스 버튼(?)을 누르면 다양한 채팅관련 메뉴가 최하단에 생성.

### 해결

1. [FrameLayout을 activity_chatting_room.xml에 추가](https://github.com/flowertaekk-dev/cloneKakaoTalk/blob/master/app/src/main/res/layout/activity_chatting_room.xml)
  * 높이는 wrap_content로 했다. 동적으로 움직여야하고, 처음에는 안보여야하기 때문에.
2. [Bottom menu용 Fragment 생성](https://github.com/flowertaekk-dev/cloneKakaoTalk/blob/master/app/src/main/java/com/example/clonekakaotalk/utils/footer/chattingRoom/FragmentChattingRoomBottomMenu.java)
  * layout에 메뉴 레이아웃 설정
3. [ChattingRoomActivity에서 Menu버튼이 눌렸을 때 Fragment를 보여주도록 한다.](https://github.com/flowertaekk-dev/cloneKakaoTalk/blob/master/app/src/main/java/com/example/clonekakaotalk/ChattingRoomActivity.java)

