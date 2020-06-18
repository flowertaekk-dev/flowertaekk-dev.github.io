---
title: "OnBackPressed event when EditText has focus"
last_modified_at: 2020-06-18
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
  - Android
tags:
  - KakaoTalk clone coding
  - EditText
toc: true
---

## EditText가 focus를 갖고 있을 때, 뒤로가기 버튼을 누르면 키보드만 사라지고 원하는 View들의 전환이 이루어지지 않음.

### 구현 중인 기능

채팅방에서 Hash tag 검색버튼을 누른 후, Back버튼을 눌렀을 때 키보드는 유지하고, footer의 view는 원래대로 돌리고 싶다. (현재는 해시태그 검색모드)

### How?

1. [EditText를 상속하는 클래스 생성](https://github.com/flowertaekk-dev/cloneKakaoTalk/blob/master/app/src/main/java/com/example/clonekakaotalk/utils/footer/chattingRoom/HashTagSearchEditText.java)
    * 다만 그냥 EditText를 상속하려고 했더니 경고가 떠서 AppCompatEditText 상속으로 했다.
2. [activity_layout에서 해당 EditText를 내가 만든 클래스로 대체](https://github.com/flowertaekk-dev/cloneKakaoTalk/blob/master/app/src/main/res/layout/activity_chatting_room.xml)
3. 그러고 나니, ChattingRoomActivity랑 내가 만든 AppCompatEditText 클래스가 어떻게 데이터를 공유할 수 있을까 이것저것 해보면서 고민...
    * 결론적으로는 정적인 클래스를 만들고, 이 static 클래스를 사용해서 데이터를 공유하도록 했다.

### 개선 가능한 부분

* 아마도 static 클래스를 이용하는 것보다 좋은 방법이 있을 듯한 느낌이 강하게 들지만, 지금은 잘 모르겠다.
