---
layout: post
title: 코딜리티
categories: [algo]
---
코딜리티 Lesson 1
--- 
1. 문제
---
- A binary gap within a positive integer N is any maximal sequence of consecutive zeros that is surrounded by ones at both ends in the   binary representation of N.

- For example, number 9 has binary representation 1001 and contains a binary gap of length 2. 
- The number 529 has binary representation 1000010001 and contains two binary gaps: one of length 4 and one of length 3. 
- The number 20 has binary representation 10100 and contains one binary gap of length 1. 
- The number 15 has binary representation 1111 and has no binary gaps. The number 32 has binary representation 100000 and has no binary   gaps.


2. 문제해석
---
- 10진수로 주어진 입력 N을  2진수로 변환 하였을 경우 위 문제에서 예로 사용한 529를 다시 예로 들어보면 1000010001로 변환 된다.
- 이 때 1 사이의 0의 갯수가 4개, 3개인 케이스가 발생하는데, 0의 갯수가 가장 많은 케이스를 반환해주는 메쏘드를 작성하면 된다.
- 주의할 점은 1사이의 0의 갯수만 해당된다는 것이다. 10000과 같은 경우는 해당되지 않는다.
- 아래 문제해결 부분을 보면 알겠지만 문제를 접했을 당 시에는 10진수를 2로 나누면서  2로 나눴을 때 나머지가 1인경우에 플래그를 세우고 그 사이의 
- 0의 갯수를 세다가 다시 나머지가 1인 경우가 발생했을 때 플래그를 닫고 그 때까지의 0의 갯수를 임시로 저장해두는 방식으로 로직을 작성하였다.
- 현재 다시 생각해보니 비트연산자를 이용했어야 더 간결하고 올바른 풀이가 되지 않았을까 싶다.

3.문제해결

```
static int solution(int N) {
		int val = 0;
		boolean flag = false;
		boolean end  = false;
		int tmp=0;
		while(N!= 1)
		{
			if(N%2==1 && flag == false)
			{
				flag=true;
			}
			else if (N%2==0 && flag ==true)
			{
				val++;
			}
			else if((N/2!=1 &&(N%2==1))  && flag == true )
			{
				tmp=val;
				if(tmp != 0)
				  val=0;
			}
			else if(N%2==1 && flag == true)
			{
				if(tmp <val)
				{
					tmp=val;
				}
				flag=false;
			}
			
			N/=2;
		}
		if(tmp <val)
		{
			tmp=val;
		}
		
		
		return tmp;
	}
```
