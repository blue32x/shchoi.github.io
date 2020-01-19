---
layout: post
title: 환경셋팅(1)
categories: [infra]
---

환경셋팅(1)
--- 
1. 설치 구성
---
- Virtual Box
- Centos7


2.설치 중 문제 발생 
---
- virtual Box shared directory 설정
```
mount -t vboxsf share /mnt/share 명령어 실행 시 v
boxsf 옵션을 못찾는 문제 발생
-> 해결 위해서는 virtualbox extension guest 설정 필요
```
- virtual Box extension guest 설정 문제
```
gui로 제공하는 기능은 사용 못하는 현상 발생
```
- 문제해결
발생한 두가지 문제 다음링크로 해결할 수 있음
[http://stevenjsmin.tistory.com/199](http://stevenjsmin.tistory.com/199)