---
layout: post
title: 코딜리티
categories: [algo]
---

코딜리티 Lesson 12
--- 
1. 문제
---

```
A prime is a positive integer X that has exactly two distinct divisors: 1 and X. The first few prime integers are 2, 3, 5, 7, 11 and 13.

A prime D is called a prime divisor of a positive integer P if there exists a positive integer K such that D * K = P. For example, 2 and 5 are prime divisors of 20.

You are given two positive integers N and M. The goal is to check whether the sets of prime divisors of integers N and M are exactly the same.

```
[풀이&문제](https://app.codility.com/demo/results/trainingFS6JHJ-B6Z/)
2. 문제해석
---
```
N개의 초콜릿이 있다. 처음 먹는 초콜릿은 0번째이며, 다음 순서는 (0+M)%N번째 초콜릿을 먹는다. (이부분을 잘못 생각했다 그냥 현재에서 n번째 초콜릿이다.) 
이미 먹어버린 초콜릿이 최초로 발견되는 순간까지 먹은 초콜릿의 수는 몇개 인가?
```

3.문제해결
---
* 아래 주석이 인코딩 오류가 발생해서 볼수 없기 때문에 남김
* sol1 : 최대 공약수를 구하고  최대공약수의 소수인 약수를 Map에 저장한 뒤 처리하려고 함  문제점은 소수를 판별하기 위해 에라토스테네스의 체를 사용하려고 하면 제약 조건 때문에
메모리 오버플로 발생 

```
1. array 정의 : array를 정의하여 체크보드를 만들었을 경우  heap memory 오류가 발생
2. map 정의 후 : 반복문으로 작성한 로직은 정상 작동하였으나 시간복잡도 O(N+M)으로 타임아웃
```

* sol2 : 두 수의 최대 공약수를 구하고  각 수와 두수의 최대공약수의 최대공약수를 구해나간다.?  사실 잘 이해가 안됨. 풀이 참고하자
내가 여기서 건진 것은 유클리드 호제법의 사용법 이었다....

* [풀이참고](https://mkki.github.io/codility/2018/05/31/codility-common-prime-divisors.html)
