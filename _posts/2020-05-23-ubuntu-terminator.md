---
title: "Terminator setting in Ubuntu"
last_modified_at: 2020-05-23
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
tags: 
  - ubuntu
  - terminator
toc: true
---

## Terminator Setting

1. 설치하기:

```terminal
$ sudo apt-get install terminator
```

2. Terminal 종료했다가 재시작: CTRL + ALT + T
3. Terminal 투명도 조절하기 (Option)

    1. Termianl에서 우클릭, Preferences 선택.
    2. Profiles -> Background 탭으로 이동.
    3. 'Transparent background' 선택.
    4. Transparency는 개인적으로 0.85정도가 괜찮은듯

4. 끝!

## Terminator 조작.

1. 풀 스크린 모드: F11
2. 수평으로 터미널 나누기: CTRL + SHIFT + O
3. 수직으로 터미널 나누기: CTRL + SHIFT + E
4. 현재 탭 닫기: CTRL + SHIFT + W
5. 새로운 탭 열기: CTRL + SHIFT + T
6. 분할된 터미널로 이동: ALT + 방향키

## Trouble Shooting(?)

'수평으로 터미널 나누기: CTRL + SHIFT + E'를 할 때 작동이 안되는 문제가 있었다.
{: .notice--info}

### 원인

ibus-emoji 설정과 동일한 단축키를 사용하고 있어서 '터미널 나누기'가 아니라 'ibus-emoji'가 실행되고 있었다.
{: .notice--warning}

### 해결

1. 'ibus-emoji' setting 화면으로 이동.

```terminal
$ ibus-setup 1
```

2. Emoji 탭으로 이동.
3. 'Emoji annotation' 값이 'CTRL + SHIFT + E' 로 되어있는지 확인.
4. '...' 눌러서 설정화면으로 이동.
5. 설정값 삭제.
6. 'OK' 버튼 클릭.
7. 끝!
