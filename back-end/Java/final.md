# final
추상이 상속을 강제하는 것이라면 final은 상속/변경을 금지하는 규제다. 이 정도로 final의 용도를 기억해두고 코드를 보자.
### 변수
```java
package org.opentutorials.javatutorials.finals;
 
class Calculator {
    static final double PI = 3.14;
    int left, right;
 
    public void setOprands(int left, int right) {
        this.left = left;
        this.right = right;
        //Calculator.PI = 6;
    }
 
    public void sum() {
        System.out.println(this.left + this.right);
    }
 
    public void avg() {
        System.out.println((this.left + this.right) / 2);
    }
}
 
public class CalculatorDemo1 {
 
    public static void main(String[] args) {
 
        Calculator c1 = new Calculator();
        System.out.println(c1.PI);
        //Calculator.PI = 10;
 
 
    }
 
}
```
변수 앞에 `final`이 붙었다. `final`로 지정된 변수의 값은 변하지 않는다.
### 객체 타입
객체 변수에 `final`로 선언하면 그 변수에 다른 참조 값을 지정할 수 없습니다. 원시 타입과 동일하게 한번 쓰여진 변수는 재변경 불가합니다. 단, 객체 자체가 immutable하다는 의미는 아닙니다. 객체의 속성은 변경 가능합니다.
```java
@Test
    public void test_final_reference_variables() {
        final Pet pet = new Pet();
//        pet = new Pet(); //다른 객체로 변경할수 없음

        pet.setWeight(3); //객체 필드는 변경할 수 있음

}
```
### 메서드
어떤 클래스를 상속하는데 그 안에 `final`메서드가 있다면, 오버라이딩으로 수정할 수 없습니다.
```java
public class Base
{
    public       void m1(){...}
    public final void m2(){...}
}

public class Derived extends Base
{
    public void m1() {...}
    public void m2() {...}
}
```
메서드 인자에 final 키워드를 붙이면, 메서드 안에서 변수값을 변경할 수 없습니다. 
```java
public class Pet {
    int weight;
    public void setWeight(final int weight) {
//        weight = 1; //final 인자는 메서드안에서 변경할 수 없음
    }
}
```
### 클래스
클래스에 `final`를 붙이게 된다면 **상속**도 불가능하다. 이렇게 하면 보안이나 효율성 측면에서 장점이 있습니다.