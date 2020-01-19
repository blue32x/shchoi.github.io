---
layout: post
title: 코딜리티
categories: [algo]
---

프로그래머스 : 다리를 지나가는 트럭
---
1. 문제
---
[https://programmers.co.kr/learn/courses/30/lessons/42583](https://programmers.co.kr/learn/courses/30/lessons/42583).

2. 문제해석
---
트럭이 다리에 진입하는 시간 1초
트럭이 다리에서 나가는 시간 1초
트럭이 진입해야하는 다리를 하나의 큐 BridgeQueue로 정의하였다. 큐의 원소는 트럭의 무게와 진입시간에 대한 정보를 가지고 있는 TruckInfo 객체이다. BridgeQueue는 다리가 최대로 견딜 수 있는 한계 무게, 현재 무게, 다리의 길이와 같은 정보를 관리하고 Queue를 멤버변수로 가지고 있다.트럭이 다리에 진입하기 전 
한계 무게와 현재 무게 + 트럭의 무게를 비교하여 진입여부를 판단하고 진입이 가능하면 Queue에 진입하는 트럭에 대한 정보를 추가한다. 트럭이 다리를 나갈 경우에는 현재무게에서 다리를 벗어난 트럭의 무게를 뺀다.
위와 같은 작업은 Queue의 원소가 0개가 될 때까지 진행한다.

3.문제해결
---
인코딩 문제로  소스에 주석은 삭제함_ 2018.01.08

```
public class Truck {
	
	 public int solution(int bridge_length, int weight, int[] truck_weights) {
	        int answer = 0;
	        int i =	0;
	        BridgeQueue bQueue = new BridgeQueue();
	        bQueue.setLengh(bridge_length); //bridge 
	        bQueue.setLimit(weight);		
	        TruckInfo tinfo = new TruckInfo();
        	tinfo.time=answer;
        	tinfo.weight= truck_weights[i];
	        //����ִ� �ʱ� ť�� �ʱⰪ ���� : Ʈ�� ���� �߰�.
        	answer++;
        	if(bQueue.add(tinfo))
        	{
        		i++;
        	}
	        while(bQueue.getCurrenctSize() != 0)
	        {
	        	
	        	bQueue.remove(answer);
	        	if(i <truck_weights.length)
    			{
		        	
	        		tinfo = new TruckInfo();
	        		tinfo.time=answer;
	        		tinfo.weight= truck_weights[i];
		        	if(bQueue.add(tinfo))
		        	{
	        			i++;
		        	}
    			}
	        	answer++;
	        }
	        
	        return answer;
	    }
	 
	 class TruckInfo
	 {
		 public int time=0;
		 public int weight=0;
	 }
	 class BridgeQueue
	 {
		 private int length ;
		 private int max_weight;
		 private int current_weight;
		 private Queue<TruckInfo> mQueue;
		
		 public BridgeQueue()
		 {
			 this.length = 0;
			 this.max_weight = 0;
			 this.current_weight=0;
			 this.mQueue=new LinkedList<TruckInfo>();
			 
		 
		 }
		 
		 public void setLengh(int length)
		 {
			 this.length=length;
		 }
		 public int getLength()
		 {
			 return this.length;
		 }
		 
		 public void setLimit(int limit)
		 {
			 this.max_weight=limit;
		 }
		
		 public boolean add(TruckInfo truck)
		 {
			 boolean flg =false;
			 if(this.max_weight < truck.weight+this.current_weight)
			 {
				 flg =false;
			 }
			 else if(this.length < this.mQueue.size())
			 {
				flg = false; 
			 }
			 else
			 {
				 this.mQueue.add(truck);
				 this.current_weight+=truck.weight;
				 
				 flg=true;
			 }
			 
			 
			 return flg;
		 }
		 
		 public void remove(int second)
		 {
			 int removedVal = 0;
			
			 if(mQueue.size() > 0)
			 {
				 TruckInfo truckInfo = mQueue.peek();
				 if(second - truckInfo.time >=length)
				 {
					 mQueue.remove();
					 current_weight-=truckInfo.weight;
				 }
			 }
			
		 }
		 public int getCurrenctSize()
		 {
			 return mQueue.size();
		 }
		 
		 
	 }

}
```