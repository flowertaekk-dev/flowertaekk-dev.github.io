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
  * git commit --amend
    * 기존 commit 수정
    * 실수로 --amend했을 경우 $ git reset --soft @{1} 로 되돌릴 수 있다.

### $ git filter-branch

  * Git의 히스토리가 필요 이상으로 길어지거나 암호 파일등을 실수로 커밋했을 때 제거하는 커맨드
    * ex) `$git filter-branch --prune-empty --index-filter 'git rm --cached --ignore-unmatch <target file>' -- --all`
  * 단점은 commit id가 변경되기 때문에 이미 공유된 커밋에 대해서는 자제하는 편이 좋다. 어쩔 수 없이 해야만 한다면, 팀원들과 공유 후에 실행하는게 절대 원칙!

#### BFG Repo-Cleaner 

  * ex) `java -jar bfg-1.13.0.jar --strip-blobs-with-ids <ids.txt> repository.git`
  * `ids.txt` 파일은 지우고자 하는 파일의 hash 값을 넣는다.
    * `$ git hash-object <file name>`
  * `repository.git` 은 `$ git clone --mirror <url>` 로 얻을 수 있다.
    * 단, repository 디렉토리를 받아오기 때문에 여기서 무언가를 변경하고 push를 하게 되면 모든 브랜치에 영향이 있을 수 있다는 점 주의!!!

## Merge

  * $ git merge -Xignore-all-space
    * 이 옵션을 통해서 공백으로 인한 충돌을 무시할 수 있다.

## diff

  * $ git diff --check
    * 추가된 공백을 확인할 수 있다. 불필요한 공백을 커밋 전에 정리할 수 있다.

## 로컬에서 깃 서버 만들어서 테스트하기

  1. `$ mkdir ~/gittest.git && cd ~/gittest.git`
  2. `$ git init --bare`
      * 비어있는 repository를 생성
  3. `$ mkdir ~/Desktop/local && cd ~/Desktop/local`
  4. `$ git clone ~/gittest.git`

## Repository 복사하기

  1. `$ git clone <url>`
  2. `$ git remote remove origin`
  3. `$ git remote add origin <new-repository-url>`
  4. 끝!
