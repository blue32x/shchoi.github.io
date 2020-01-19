---
layout: post
title: 코딜리티
categories: [algo]
---

코딜리티 Lesson 10
--- 
1. 문제
---
Counter Factors  : 효율적으로 약수의 갯 수 를 구하라......


2. 문제해석
---
주어진 입력 파라미터 N을 구성하는 약수의 갯수를 구하라.약수는  양수 D로 N을 나눴을 경우 나머지가 0이라면   (D,N/D)의 쌍으로 이뤄진다.

HashMap을 통해서 약수의 쌍을 관리하고 반복문의 인덱스 D가  기적재되어있는 N/D보다 커지면 반복문을 탈출한다. 여기서 시간복잡도가 O(N)보다 작다.

특수한 경우  MAX_INT, 780291637,5621892 와 같은 경우  D 와 N/D를 비교하기 위해서는 결국 N번 모두 순회하여야 하므로 시간복잡도가 O(N)에 가까워진다.

이 문제를 해결하기 위해서 순회하는 범위를 D만큼 나눠서 순회하도록 로직을 구현했다.       


3.문제해결
---
시간복잡도 O(sqrt(N))

```
	int solution(int N)
		{
			//5621892
			//780291637(소수)
			//MAX_INT (소수)
			/* 
			 * O(sqrt(N))
			 * 해당 로직의 문제는   소수일 경우 혹은 나눠 떨어지는 숫자들의 텀이 클 수록 O(N)이 증가함
			 * worst case = 0(N)
			 * 
			 * 
			 */
			Map<Integer,Integer> hMap = new HashMap<Integer,Integer>();
			
			for(int idx=1; idx<=N/idx ;idx++)
			{
				if(idx <=0)
				{
					break;
				}
				if(!hMap.containsKey(idx))
				{
					if(N%idx == 0)		
					{
						
						hMap.put(idx, N/idx);
						System.out.println("Set : "+idx+" "+N/idx);
						hMap.put(N/idx,idx);
					//	N/=idx;
					}
					else
					{
						continue;
					}
				}
				else
				{
					if(idx >=hMap.get(N/idx))
					{
						break;
					}
				}
				
			}
			
			return hMap.size();
		}
```