---
title: "OSS 도전하기"
last_modified_at: 2020-06-21
header:
  overlay_color: "#333"
categories:
  - Development
  - OSS
tags:
  - OSS
toc: true
---

Open Source Software 도전하기

## Git 설정

### upstream 설정하기

fork한 upstream의 repository의 변화를 수시로 간편하게 적용할 수 있도록 하기위한 작업.

1. [git에 remote 추가하기](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/configuring-a-remote-for-a-fork)
```cmd
$ git remote add upstream <original repository> # upstream도 네이밍은 자유지만, 컨벤션인듯하다.
```
2. [original repository에서 바뀐 코드 적용](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/syncing-a-fork)
```cmd
$ git fetch upstream
$ git checkout master
$ git merge upstream/master
```
3. upstream 설정해두기
```cmd
$ git branch --set-upstream-to=upstream/master master
```

## 참고자료

* [OSS Guide](https://opensource.guide/ko/how-to-contribute/)
    * 여기를 보면서 많이 참고.
* [Git 세팅부터 PR 넣기까지 동영상자료](https://egghead.io/lessons/javascript-setting-up-the-project-locally)
    * GitHub에 대한 전반적인 설명부터 PR까지 자세하게 알려준다.

