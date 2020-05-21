---
title: "Git command"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - git
  - VCS
toc: true
---

## Check Logs

  * $ git log
    * -L option : 특정 함수의 history를 확인할 수 있다. 
      * ex) $ git log -L : function name : file name
    * --merge option (when conflict) : 충돌이 발생한 파일이 속한 commit만 보여준다.
    * -p option (when conflict) : 충돌이 발생한 파일의 변경사항만 볼 수 있다.
  * $ git show : 각 commit에서 수정된 코드까지 확인할 수 있다. 
    * tip) $ git log HEAD^  : 끝에 ^ 를 붙이면 해당 commit의 부모를 붙인다.
    * tip) $ git log HEAD^2 : HEAD의 두 번째 부모를 의미 (아직 잘 모르겠다)
    * tip) $ git log HEAD~  : HEAD^ 와 같은 결과를 볼 수 있다.
    * tip) $ git log HEAD~2 : HEAD로부터 이전 2개의 commit을 제외한 다른 log를 볼 수 있다. (이것도 아직 잘 모르겠다)

## Range

  * Double dot
    * ex) $ git log origin/master..HEAD
      * origin/master에는 없고, 현재 HEAD에만 있는 commit들을 확인할 수 있다.
  * Triple Dot
    * ex) $ git log master...dev
      * master와 dev 브런치에 존재하지 않는 commit들을 확인 할 수 있다.

## Stash

### $ git stash

### $ git stash apply

  * --index 옵션으로 stash한 파일들의 Staged 상태까지 적용할 수 있다.

### $ git stash drop

  * $ git stash apply는 stash 기록을 지우지 않기 때문에 직접 drop해야만 한다.

### $ git stash pop

  * $ git stash apply + $ git stash drop stash@{n}

### $ git stash list

  * stash 리스트를 보여준다.

## Search (검색)

  * $ git grep
    * 성능이 좋다고 한다.

## Commit 관리

  * git rebase -i HEAD~n

## Merge

  * $ git merge -Xignore-all-space
    * 이 옵션을 통해서 공백으로 인한 충돌을 무시할 수 있다.