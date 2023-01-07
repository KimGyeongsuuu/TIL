# JVM(Java Virtual Machine)
`Java Virtual Machine`의 약자로 직역하면 `자바를 실행하기 위한 가상 머신`이라고 할 수 있다.<br>
Java는 OS에 종속적이지 않다는 특징을 가졌다. OS에 종속받지 않고 JAVA를 실행하려면 OS위에서 JAVA를 실행해야한다. 그것이 `JVM`이다.<br>
즉, OS에 종속받지 않고 CPU가 Java를 인식하여 실행할 수 있게 하는 것이 `JVM`이다.

![java](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F0kg24%2Fbtq4YOOQH4J%2FEF2ISOpkYA36a1flwtLEmK%2Fimg.png)

Java 소스코드, 즉 원시코드(`*.java`)는 CPU가 인식하지 못하므로 기계어로 컴파일 해야 한다.
하지만 JAVA는 JVM으로 OS에 도달하기 때문에 JVM이 인식할 수 있는 Java bytecode(`*.class`)로 변화되고 OS가 인식할 수 있는 기계어로 변환된다.

**Java compiler**가 `.java`파일을 `.class`라는 **Java bytecode**로 변환시킨다.<br>
변환된 Java bytecode는 기계어가 이니기 때문에 OS에서 바로 실행되지는 않는다.<br>
이 때, JVM이 OS가 bytecode를 이해할 수 있도록 해석해준다. 따라서 bytecode는 JVM위에서 OS에 상관없이 실행될 수 있다.

OS에 종속적이지 않고, JAVA파일만 만들수 있으면 언제든지 JVM 위에서 실행시킬 수 있다.


### 컴파일
아래의 코드는 Java Compiler에 의해 `.java`파일을 `.class`의 bytecode로 만드는 과정이다.


**예제**
```java
public class test {
    public static void main(String[] args) {
        System.out.println("Hello World");
    }
}
```

### 바이트코드
가상 컴퓨터에서 돌아가는 실행 프로그램을 위한 이진 표현법<br>
자바 바이트코드는는 `JVM`이 이해할 수 있는 언어로 변환된 자바 소스코드를 말한다.<br>

바이트코드는 다시 실시간 변역기 또는 JIT 컴파일러에 의해 바이너리 코드로 변환된다.<br>
```
바이너리 코드란?

바이너리 코드 또는 이진코드라고 함
컴퓨터가 이해할 수 있는 0과1로 구성되어 있는 이진코드
```
```
기계어란?

0과1로 이루어진 바이너리 코드다.
기계어가 바이너리코드로 이루어져있는거지, 모든 바이너리코드가 기계어는 아니다.
기계어는 특정한 언어가 아니라 CPU가 이해할 수 있는 명령어 집합체이다.
```