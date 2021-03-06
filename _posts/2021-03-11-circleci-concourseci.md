---
title: "CICD툴 비교: CircleCI vs. ConcourseCI"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - CICD
toc: true
---

## CICD 란?

지속적인 통합(Continuous Integration)과 지속적인 배포(Continuous Deployment) 를 합쳐서 CICD 라 부른다.

* `CD` 는 `Continuous Delivery` 의 약자로도 쓰인다. 늬앙스의 차이는 있으나 결국 파이프라인의 자동화라는 맥락에서는 동일.

## CICD 툴 비교

CICD를 도입하기 위해 조사 중인 2가지 툴인 `CircleCI` 와 `Concourse CI` 에 대해서 비교

| 비교 | CircleCI | Concourse CI |
|:--:|:---:|:---:|
| 초기 셋업 | 아주 쉽다. | 상대적으로 쉽지는 않다 |
| Git 연계 | GitHub 와의 연계가 직관적이라는 평이 있음 | `set_pipeline` 단계를 통해서 파이프 라인을 자동으로 설정한다. |
| DataBase | 사용 안 해도 운용가능?  | PostgreSQL 사용. 공식문서에도 메모리에 관한 코멘트가 있음. [링크](https://concourse-ci.org/postgresql-node.html#db-resource-utilization) |
| OS | ? | 공식문서상 테스트/서포팅하는 리눅스는 데비안 계열 |
| 도커 연계 | 도커 이미지를 캐싱하는데 성능상 문제가 있다는 블로거들이 몇몇 있었지만, 공식문서상으로는 캐싱을 문제없이 제공한다고 되어 있음.  | 도커 연계에 대한 특별한 이슈사항은 없는듯 |
| 관련 블로그 | 한국어로도 관련 포스팅이 많다 | 한국어로는 흔치 않다. 외국자료는 많지만. (페이지 하단에 있는 공식튜토리얼이 Goooooood!!) |

## 그 외 특징들

### CircleCI

* Git 에 연동하는 과정에서 기본 세팅이 이루어진 yaml 생성 등의 조작이 이루어진다.
* 다양한 캐시 기능을 통해서 속도 개선 등이 가능하다.
* SSH 를 통해 build issue 디버깅이 가능하다.
* 여러 프로젝트를 갖고 있을 때 병렬 처리가 가능하다. (한 번에 여러 프로젝트를 빌드 및 테스트 가능.)
    * https://circleci.com/docs/2.0/about-circleci/?section=getting-started#benefits-of-circleci
* `GitHub + EC2 + CircleCI` 를 구현하려면 아마도 이 두 가지 패턴을 사용해야 할 듯. (어느게 좋을지는 생각과 공부를 해봐야 할 듯)
    1. circle-ci가 build -> AWS S3 에 build 결과물 저장 -> AWS Code Deploy가 S3에서 build 결과물을 불러와서 배포 시작
    2. circle-ci가 build -> AWS Security Group 에 circle-ci 가 EC2 에 접근할 수 있도록 권한 부여 -> EC2 에 직접 build 결과물 scp
* SSH 로 직접 circle-ci server 에 접속해서 디버깅이 가능하다!! 이건 상당히 편리한 기능인듯!

### Concourse CI

* 모든 `Task` 는 컨테이너 내부에서 실행된다. refs: [Every task in Concourse runs within a "container"](https://concoursetutorial.com/basics/task-hello-world/)
* `yaml` 로 CICD 툴을 버전 관리 할 수있다는 것도 좋다.
* Git 연동을 하려면 YAML을 통한 resource 설정이 필요. [stackoverflow 관련 내용](https://stackoverflow.com/questions/51310079/concourse-webhook-to-git) , [git-resource 설정 리드미](https://github.com/concourse/git-resource)


## 블로그 정리

* [circleci](https://flowertaekk.tistory.com/17)
* [Concourse CI](https://flowertaekk.tistory.com/18)

## 공식 튜토리얼

* [CircleCI](https://circleci.com/docs/2.0/tutorials/)
* [Concourse CI](https://concoursetutorial.com/)


