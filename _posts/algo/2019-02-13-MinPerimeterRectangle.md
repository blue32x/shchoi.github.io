---
layout: post
title: 코딜리티
categories: [algo]
---

코딜리티 Lesson 10
--- 
1. 문제
---
MinPerimeterRectangle  : An integer N is given, representing the area of some rectangle.

The area of a rectangle whose sides are of length A and B is A * B, and the perimeter is 2 * (A + B).

The goal is to find the minimal perimeter of any rectangle whose area equals N. The sides of this rectangle should be only integers.

For example, given integer N = 30, rectangles of area 30 are:

(1, 30), with a perimeter of 62,

(2, 15), with a perimeter of 34,

(3, 10), with a perimeter of 26,

(5, 6), with a perimeter of 22.......


2. 문제해석
---
2019-02-11에 포스트했던 CounterFactors의 연장 문제이다 . 문제에서 하고 싶은 말은 약수의 짝 중에서 2*(A+B)가 가장 작은 값을 구해라!

1번의 문제에서 변한 로직은  최솟값을 구하는 로직이 추가되고 메쏘드의 반환값으로 hashMap의 크기가 아닌 최솟값을 반환한다.


3.문제해결
---
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
			int minVal= Integer.MAX_VALUE;
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
						//System.out.println("Set : "+idx+" "+N/idx);
						if(minVal >= 2* (idx +N/idx))
						{
							minVal = 2* (idx +N/idx);
						}
						
						
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
			
			return minVal;
		}
```