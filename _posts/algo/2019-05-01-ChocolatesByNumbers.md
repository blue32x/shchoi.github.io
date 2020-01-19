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
Two positive integers N and M are given. Integer N represents the number of chocolates arranged in a circle, numbered from 0 to N − 1.

You start to eat the chocolates. After eating a chocolate you leave only a wrapper.

You begin with eating chocolate number 0. Then you omit the next M − 1 chocolates or wrappers on the circle, and eat the following one.

More precisely, if you ate chocolate number X, then you will next eat the chocolate with number (X + M) modulo N (remainder of division).

You stop eating when you encounter an empty wrapper.

For example, given integers N = 10 and M = 4. You will eat the following chocolates: 0, 4, 8, 2, 6.

The goal is to count the number of chocolates that you will eat, following the above rules.

Write a function:

class Solution { public int solution(int N, int M); }

that, given two positive integers N and M, returns the number of chocolates that you will eat.

For example, given integers N = 10 and M = 4. the function should return 5, as explained above.

Write an efficient algorithm for the following assumptions:

N and M are integers within the range [1..1,000,000,000].

```
[참고](https://app.codility.com/demo/results/trainingBHE2PQ-6TD/)

2. 문제해석
---
```
N개의 초콜릿이 있다. 처음 먹는 초콜릿은 0번째이며, 다음 순서는 (0+M)%N번째 초콜릿을 먹는다. (이부분을 잘못 생각했다 그냥 현재에서 n번째 초콜릿이다.) 
이미 먹어버린 초콜릿이 최초로 발견되는 순간까지 먹은 초콜릿의 수는 몇개 인가?
```

3.문제해결
---
* 아래 주석이 인코딩 오류가 발생해서 볼수 없기 때문에 남김
* sol1 : 이미 먹었는지를 체크할 수 있는 보드를 만들어 기록하는 컨셉

```
1. array 정의 : array를 정의하여 체크보드를 만들었을 경우  heap memory 오류가 발생
2. map 정의 후 : 반복문으로 작성한 로직은 정상 작동하였으나 시간복잡도 O(N+M)으로 타임아웃
```
* sol2 : lesson 주제에 맞는 유클리드 호제법 응용

```
sol2의 말이 유클리드 호제법 응용이지 반복문의 로직을 재귀함수로 변경한 것 뿐 따라서 동일한 시간 복잡도가 발생하고 입력값에 따라
heap memory overflow 발생
```
* sol3 : 전체 초콜릿의 갯수 N과 초콜릿을 먹을 인터벌?을 가리키는 M의 최대 공약수를 구한 후 최초로  초콜렛을 먹은 지점인 0으로 돌아올 때를 찾기위해
N/G(N,M) 연산을 한다.

* [참고](https://ergate.tistory.com/entry/Codility-ChocolatesByNumbers-1)

```
		private static HashMap<Integer,Integer> map = null;
		
		public static int solution(int 	N, int M) throws InterruptedException
		{
			int results=1;

			map= new HashMap<Integer,Integer>();
			
			int current = M;
			

			
			
			
			
			return N/gcd(N,M);
		}
		
		public static int gcd(int p, int q)
		 {
			if (q == 0) return p;
			return gcd(q, p%q);
		 }
		
		public static int getNextIndex(int current, int N,int M) throws InterruptedException
		{
			if(map.containsKey(current))
			{
				return 0;
			}
			else
			{
				System.out.println("current Idx : "+ current);
				Thread.sleep(1000);
				map.put(current, current);
				return getNextIndex((current+M)%N,N,M)+1;
			}
		}
	}
```