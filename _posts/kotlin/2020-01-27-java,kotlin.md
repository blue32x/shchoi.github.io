---
layout: post
title: kotlin (1)
categories: [kotlin]
---


1.서론
---
java와 kotlin 뭐가 다를까? 이직 후 처음 접하게 된 kotlin과 계속 써왔지만 아직도 공부할 게 많은
자바를 비교하면서 포스팅하면 도움이 많이 될 것 같아서 포스팅 시작.
 
2.프로그래밍 언어의 왕도는 역시 Hello Wold
---
Java
```
public class JavaTest {
    final static String name= "sh.choi";
    public static void main(String[] args){
        System.out.println("Hello Wolrd "+name);
    }
}
```

Kotlin
```
val name="sh.choi"

fun main(args : Array<String>){
    println("Hello World $name")
}
```

위의 두 소스는 `Hello world sh.choi`라는 동일한 결과를 출력한다. 

차이가 보이는가? name이라는 변수의 선언 방식, main method의 위치, method의 입력 파라미터
그리고 출력 시 앞에서 정의한 name을 사용하는 방식이 달라졌다. 

1. 변수 선언

```
val -> value : null type이 불가능 
var -> variable : null type 허용
```

2. main method 위치

```
*.kt 파일의 top level에 main function을 작성 할 수 있다. 
```

3. method 정의 방법

```
method의 return type을 명시 하던 위치에 fun이라는 keyword가 들어감
입력파라미터도  type variabaleName과 같은 형식이 아닌 variableName:type 과 같은 형식으로 바뀜


 자바 :   [returnType] [methodName] (variableType [variableName])
                                ↓
 코틀린 :  fun [methodName]([variableName]:variableType):[returnType]

```

4. 변수 사용방법.
 
```
String 내부에서 사용하고자 하는 변수 앞에 $를 함꼐 붙여 주면 스트링 내부에서 변수를 사용할 수 있음

```

