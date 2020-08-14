---
title: "Spring Boot"
header:
  teaser: "assets/images/markup-syntax-highlighting-teaser.jpg"
categories:
  - Development
tags:
  - Java 
  - SpringBoot
toc: true
---

## Spring Boot

### h2 in-memory DB 사용하기

* application-properties파일에 설정 추가

```
spring.h2.console.enabled=true
```

* http://localhost:port/h2-console로 접속
* JDBC URL에 아래와 같이 설정

```
jdbc:h2:mem:(SpringBoot로그를 보고 설정)
```
