# Static
Static이라는 키워드를 사용하여 Static변수와 Static메소드를 만들 수 있는데 다른말로 정적필드와 정적 메소드라고도 하며 이 둘을 합쳐 정적 멤버라고 합니다. 

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fefeoz2%2FbtqDsOt6are%2F0masSctPvO9gk0PkTY7tSK%2Fimg.png)

### 선언
필드나 메소드를 생성 시 인스턴스로 생성할 것인지 정적으로 생성할것인지에 대한 판단 기준은 공용으로 사용하는냐 아니냐로 나뉜다.

 정적으로 생성하려면 필드와 메소드 선언 시 static이라는 키워들를 추가적으로 붙이면 됩니다. 
```java
static int num = 0; //타입 필드 = 초기값
public static void static_method(){} //static 리턴 타입 메소드 {}
```