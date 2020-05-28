---
title: "Layout border design in Android"
last_modified_at: 2020-05-24
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
  - Android
tags:
  - KakaoTalk clone coding
  - border design
toc: true
---

## 카카오톡 친구목록 ExpandableListView 구현에서 Layout border 디자인 구현하기

### 카카오톡 화면

![image-center]({{ https://flowertaekk-dev.github.io }}{{ android-border-design }}/assets/images/cloneKakaoTalk/friendsList.png){: .align-center}

  (스샷이 잘못 찍혔는지 Favorites와 Channels사이에 border가 안 보이지만, 있다.)
### Child Component와 Parents Component 사이에는 border를 넣고 싶지 않았기 때문에, Parents Component의 위쪽 border만 표시하도록 하고 싶었다.

  * 처음에는 아래쪽 border만 없어지게 하는 방법이 있지 않을까 해서 이것저것 알아봄. 실패.
  * 결과적으로, 위쪽 border는 남겨놓고, 아래쪽 border만 안 보이게 하는 방법은 못 찾았다.
  * 그래서 전부 다 없애고, 위쪽 border만 그리는 방법으로 변경.

```xml
android:divider="#00000000"
android:childDivider="#00000000"
```

  * 재사용이 가능한 방법으로, custom_border.xml을 따로 만들어놓고 불러다 쓰는 방법으로 결정.

```xml
<?xml version="1.0" encoding="utf-8
<layer-list xmlns:android="http://schemas.android.com/apk/res/android" >
    
    <item
        android:bottom="-2dp" <!-- 음수 값을 설정하면 border를 표시하지 않음  -->
        android:left="-2dp"
        android:right="-2dp"
        android:top="1dp">
        <shape android:shape="rectangle" >
            <stroke  <!-- border의 두께와 색상을 지정  -->
                android:width="1dp"
                android:color="#dcdcdc" />
                
            <solid android:color="#00000000" /> <!-- 배경색 지정(여기서는 투명으로)  -->
        </shape>
    </item>
     
</layer-list>
```

  * ListView에서 목록을 클릭했을 때, 효과가 있는거 같아서 border가 순간 두꺼워지는 듯이 보이는 문제 발견.
    * 제거하기 위해 ExpandableListView에 설정 추가.

```xml
android:listSelector="@android:color/transparent"
```

  * 끝 
