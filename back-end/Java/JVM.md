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

### JIT 컴파일러
JIT컴파일러는 동적 번역이라고 한다.<br>
JIT컴파일러는 프로그램을 실제로 실행하는 시점에 기계어로 변역하는 컴파일러이다.<br>

인터프리터 방식의 단점을 보완하기 위해 도입되었다.<br>
인터프리터 방식으로 실행하다가 적절한 시점에 바이트 코드 전체를 컴파일하여 기계어로 변경하고, 이후에는 해당 더 이상 인터프리팅 하지 않고 기계어로 직접 실행하는 방식이다.



### JVM 구성요소
![jvm](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FtclVx%2Fbtq4Xfml6Dy%2Fnzb5xxlGG1fr5iBGUMv77K%2Fimg.png)

JVM은 크게 아래와 같이 이루어져 있다.

+ 클래스 로더(Class Loader)

+ 실행 엔진(Execution Engine)
    + 인터프리터(Interpreter)

    + JIT 컴파일러(Just-in-Time)

    + 가비지 콜렉터(Garbage collector)

+ 런타임 데이터 영역 (Runtime Data Area)


**클래스 로더**

JVM 내로 클래스 파일(*.class)을 로드하고, 링크를 통해 배치하는 작업을 수행하는 모듈이다.

**실행 엔진**

클래스를 실행시키는 역할이다.

**인터프리터**

실행 엔진은 자바 바이트 코드를 명령어 단위로 읽어서 실행한다.
하지만 한 줄씩 수행하기 때문에 느리다는 단점이 있다.


**JIT(Just-In-Time)**

인터프리터 방식으로 실행하다가 적절한 시점에 바이트 코드 전체를 컴파일하여 기계어로 변경하고, 이후에는 해당 더 이상 인터프리팅 하지 않고 기계어로 직접 실행하는 방식이다.

**가비지 콜렉터**

더이상 사용되지 않는 인스턴스를 찾아 메모리에서 삭제함.



