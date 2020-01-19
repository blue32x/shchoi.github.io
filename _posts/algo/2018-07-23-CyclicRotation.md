---
layout: post
title: 코딜리티
categories: [algo]
---

코딜리티 Lesson 2
--- 
1. 문제
---
An array A consisting of N integers is given. 

Rotation of the array means that each element is shifted right by one index, and the last element of the array is moved to the first place.

For example, the rotation of array A = [3, 8, 9, 7, 6] is [6, 3, 8, 9, 7] (elements are shifted right by one index and 6 is moved to the first place).


2. 문제해석
---
입력은 배열 A, 정수 형 K이다.쉽게 말하면 배열 A를 를 오른쪽으로 K만큼 순환시켜라!

예를 들어서  {3,8,9,7,6}  K=3
  
        {6,3,8,9,7}  

        {7,6,3,8,9}

      결과  : {9,7,6,3,8}
      


3.문제해결
---
진짜 단순하게 k가 0이 될 때까지 오른쪽으로 한칸 씩 이동 시키고 배열의 경계를 넘어간 숫자를 임시로 선언한 변수에 저장하고 있다가.
이동이 완료된 배열의 첫번째 저장소에 저장한다.
뭔가 더 쉬운 방법이 있을 것 가은데  당 시에는 생각이 나지 않아서  아래와 같이 처리했다.

```
		 if(A.length ==0)
		 {
			 return A;
		 }
		 
		 int[] B=A.clone();
		 
		 while((K--) != 0)
		 {
			 int shiftedNum=0;
			 shiftedNum=A[A.length-1];
			 for(int i=0; i<A.length-1; i++)
			 {
				 A[i+1]=B[i];
			 }
			 A[0]=shiftedNum;
			 B=A.clone();
		 }
		 
		 return A;
	    }
```