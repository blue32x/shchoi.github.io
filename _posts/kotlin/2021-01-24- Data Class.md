---
layout: post
title: data Class
categories: [kotlin]
---

 
1.코틀린 data Class 
---
class가 데이터를 저장하는 역할만을 수행한다면 toString, equeals, hashCode를 반드시 오버라이드해야 한다.
물론 IDE에서 자동으로 정의해수고 정확성과 일관성을 검사해준다.
코틀린은 data라는 변경자를 클래스 앞에 붙이면 필요한 메소드를 컴파일러가 자동으로 만들어준다.
data 변경자가 붙은 클래스를 데이터 클래스라고 부른다.

ex)
```
data class Client(val name: String, val postalCode: Int)
```
- 인스턴스간 비교를 위한 equeals
- HashMap과 같은 해시 기반 컨테이너에서 키로 사용할 수 있는 hashCode
- 클래스와 각 필드를 선언 순서대로 표시하는 문자열 표현을 만들어주는 toString

코틀린은 data class의 프로퍼티들을 읽기전용으로 만들어 불변 클래스로 만들라고 권장한다.

- 멀티 쓰레드 환경에서 불변 객체를 다른 쓰레드가 변경할 수 없기 때문데 동기화 필요성이 줄어든다
- 데이터를 추론하기 쉽다.
- 불변 객체를 쉽게 사용하기 위해 copy라는 메쏘드를 제공하여 원본에 영향을 주지 않는 기능을 제공한다.

이슈
springboot 환경에서 data class를 api의 response로 셋팅했을 경우
실제 데이터가 있음에도 swagger의 응답으로 response가 비워져서 옴
java의 경우 lombok annotation @RequiredArgument, @getter, @setter를 이용하여 해결
했지만 kotlin의 경우 lombok을 사용하지 않음
각 프로퍼티의 default value를 설정하거나 default constructor를 새로 셋팅 하는 것으로 해결했다.

Sol1
```
data class Client(val name: String ="", val postalCode: Int=0)
``` 
 
Sol2
```
data class Client(val name: String, val postalCode){
    constructor() : this("",0)
}

```


참조
kotlinInAction


