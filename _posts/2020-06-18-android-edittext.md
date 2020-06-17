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

검색필요. EditText를 상속하는 클래스를 만드는 수 밖에 없나?
