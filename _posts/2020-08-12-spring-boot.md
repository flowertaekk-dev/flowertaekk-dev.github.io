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

### Test

* @SpringBootTest
  * 모든 bean을 주입하기 때문에 속도가 느리다. (아직은 개발 초기라 별 문제 없어보인다.)
* @WebMvcTest
  * 가볍고 빠르게 테스트 가능하지만, @Controller 관련 Bean만 주입해준다. 그래서 @Service 등에서 터지는 문제가 생겼고, 상당히 헤맸다. 주의..
