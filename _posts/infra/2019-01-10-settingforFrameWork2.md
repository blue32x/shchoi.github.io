---
layout: post
title: 환경셋팅(2)
categories: [infra]
---

환경셋팅(2)
--- 
1. 설치 구성
---
- Virtual Box
- Centos7
- framework
- aws로 기동 중인 oracle server
- tomcat7

2.설치 내용 
---
- java 1.8.0 설치 및 경로

```
 1. 설치 명령어
 user$ yum install java-1.8.0-openjdk-devel.x86_64
 2. 설치된 경로
 user$ ls /usr/lib/jvm/jre-1.8.0-openjdk-1.8.0.191.b12-1.el7_6.x86_64
 ```

- tomcat 7 설치 및 셋팅
- 설치주소 [tomcat7](https://tomcat.apache.org/download-70.cgi)

```
1. 2019-01-09에 포스팅한 공유폴더를 통해 가상화한 linux에 설치파일 전달.
2. 제공받은 메뉴얼에 따라 특정위치에서 압축해체
3. tomcat7_admin , tomcat7_online 각각의 역할 마다 서버생성
```
- tomcat 7 new info

```
1. JNDI란?Java Naming and Directory Interface 이며 아래  JNDI정보 를 참조

  1.이점 : 유지보수 용이, 로드밸런싱용이, 다수의 datasource 공유 가능,
  
  
2. Server.xml,Context.xml 차이
  
  1.Server.xml	: Was에서 공통으로 사용하는 설정 
  
  2.Context.xml : 서버 위에서 구동되는  application을 위한 설정
  
  3.server.xml에 reource 등록 후 context.xml에서 resource link로 참조 가능
  
3. globalResource 설정
```

2.참조 
---

#1 JNDI정보
[http://blog.naver.com/PostView.nhn?blogId=parkkcy&logNo=20128228201](http://blog.naver.com/PostView.nhn?blogId=parkkcy&logNo=20128228201)

#2 server.xml 자원등록
[설정 참고자료](https://github.com/Wonjune/DatasourceServlet/wiki/3.-Tomcat-%EC%84%9C%EB%B2%84%EC%9D%98-DataSource-%EC%82%AC%EC%9A%A9%ED%95%98%EA%B8%B0)