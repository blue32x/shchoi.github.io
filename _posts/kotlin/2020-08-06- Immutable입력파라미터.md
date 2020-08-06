---
layout: post
title: Immutable 입력파라미
categories: [kotlin]
---

 
1.코틀린 메쏘드 입력 파라미터
---
코틀린에서는 메쏘드의 입력파라미터는 불변이다. 리팩토링 하다가 자바처럼 입력파라미터로 받은 변수의
값을 변경하는 로직을 넣었는데 오류처리 하길래 찾아봄

Java
```
private void test(int a){
    a+=1  //가능
}
```

Kotlin
```
private fun test(a: Int){
    a+=1  //불가능
}
```

코틀린은 왜 메쏘드의 입력파라미를 불변으로 강제하는가?
1. runtime 시 점에 비용이 많이 든다.
2. 대부분의 사람들이 매개변수를 참조로 전달한다고 생각함 (지원안함)

참조


[kotlinblog](https://blog.jetbrains.com/kotlin/2013/02/kotlin-m5-1/?_ga=2.231515743.1902679046.1596696070-410032598.1596696070)


