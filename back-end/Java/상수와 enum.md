# 상수와 enum
### 상수
상수는 변하지 않는 값이다. 아래에서 좌항은 변수이고 우항은 상수이다.
```java
int x = 1;
```
상수의 특성을 이용해서 이런 로직을 작성할 수 있다.
```java
package org.opentutorials.javatutorials.constant2;
 
public class ConstantDemo {
    public static void main(String[] args) {
        /*
         * 1. 사과
         * 2. 복숭아
         * 3. 바나나
         */
        int type = 1;
        switch(type){
            case 1:
                System.out.println(57);
                break;
            case 2:
                System.out.println(34);
                break;
            case 3:
                System.out.println(93);
                break;
        }
    }
 
}
```
변수도 상수가 될 수 있다. 변수를 지정하고 그 변수를 `final`로 처리하면 한 번 설정된 변수의 값은 더 이상 바뀌지 않는다. 
```java
private final static int APPLE = 1;
private final static int PEACH = 2;
private final static int BANANA = 3;
```
프로그램이 커지면서 기업에 대한 상수가 필요해졌다

`APPLE`이라는 변수이름이 겹치게 되었다.
```java
package org.opentutorials.javatutorials.constant2;
 
public class ConstantDemo {

    // fruit
    private final static int APPLE = 1;
    private final static int PEACH = 2;
    private final static int BANANA = 3;

    // company
    private final static int GOOGLE = 1;
    //private final static int APPLE = 2;
    private final static int ORACLE = 3;

    public static void main(String[] args) {
        int type = APPLE;
        switch(type){
            case APPLE:
                System.out.println(57);
                break;
            case PEACH:
                System.out.println(34);
                break;
            case BANANA:
                System.out.println(93);
                break;
        }
    }
 
}
```
이름이 중복될 확률을 낮출 수 있다. 이러한 기법을 네임스페이스라고 한다. 그렇게 하면 상수가 너무 지저분하다. 이러한 상황에서는 인터헤이스를 사용할 수 있다.
```java
    // fruit
    private final static int FRUIT_APPLE = 1;
    private final static int FRUIT_PEACH = 2;
    private final static int FRUIT_BANANA = 3;

    // company
    private final static int COMPANY_GOOGLE = 1;
    //private final static int COMPANY_APPLE = 2;
    private final static int COMPANY_ORACLE = 3;
```
인터페이스를 사용하였다.
```java
package org.opentutorials.javatutorials.constant2;
 
interface FRUIT{
    int APPLE=1, PEACH=2, BANANA=3;
}
interface COMPANY{
    int GOOGLE=1, APPLE=2, ORACLE=3;
}
 
public class ConstantDemo {
     
    public static void main(String[] args) {
        int type = FRUIT.APPLE;
        switch(type){
            case FRUIT.APPLE:
                System.out.println(57+" kcal");
                break;
            case FRUIT.PEACH:
                System.out.println(34+" kcal");
                break;
            case FRUIT.BANANA:
                System.out.println(93+" kcal");
                break;
        }
    }
}
```
훨씬 깔끔하다. 접미사로 이름을 구분했던 부분이 인터페이스로 구분되기 때문에 언어의 특성을 보다 잘 살린 구조가 되었다. 인터페이스를 이렇게 사용할 수 있는 것은 인터페이스에서 선언된 변수는 무조건 public static final의 속성을 갖기 때문이다.

### enum란?
`enum`은 열거형(enumerated type)이라고 부른다. 열거형은 서로 연관된 상수들의 집합이라고 할 수 있다. 어떤 클래스가 상수만으로 작성되어 있으면 반드시 class로 선언할 필요는 없습니다. 이럴 때 class로 선언된 부분에 `enum`이라고 선언하면 이 객체는 상수의 집합이라고 명시적으로 나타냅니다.

### 특징
1. 클래스를 상수처럼 사용 할 수 있다.
    + 아래의 코드는 `Enum Class`의 예제이다.
    ```java
    public enum  Rank {
    	THREE(3, 4_000),
    	FOUR(4, 10_000),
    	FIVE(5, 30_000);
    
    	private final int match;
    	private final int money;
    	private int count;
    
    	Rank(int match, int money) {  // Default 생성자는 private 으로 설정되어 있음.
    		this.match = match;
    		this.money = money;
    	}
    ```
2. 
3. 서로 관련 있는 상수 값들을 모아 `enum`으로 구현하는 경우 유용하다.
4. 클래스와 같은 문법 체계를 따른다.
5. 상속을 지원하지 않는다.
    + 모든 `enum`들은 내부적으로 `java.lang.enum`클래스에 의해 상속된다.
    자바는 다중 상속을 지원하지 않기 때문에 Enum은 다른 클래스를 상속받을 수 없다.
    + 기존에 상속받고 있는 클래스가 존재하기 때문에 다중 상속은 지원하지 않지만 다양한 인터페이스 들은 구현할 수 있다.

### Enum의 내부 Api
위에서 언급한 `java.lang.Enum`클래스를 기본적으로 상속받고 있기 때문에 아래의 세가지 메소드를 지원한다. (부모 클래스의 메소드라 사용 가능하다.)