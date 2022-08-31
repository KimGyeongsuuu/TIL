# Object
자바에서 상속이란 필수이다. 여러분이 상속하건 하지 않았건 기본적으로 상속을 하게 된다.  
### java.lang.Object 클래스
java.lang 패키지 중에서도 가장 많이 사용되는 클래스는 바로 Object 클래스입니다.
Object 클래스는 모든 자바 클래스의 최고 조상 클래스가 됩니다.
따라서 자바의 모든 클래스는 Object 클래스의 모든 메소드를 바로 사용할 수 있습니다.
<hr>

### toString() 메소드
`toString()` 메소드는 해당 인스턴스에 대한 정보를 문자열로 반환합니다.
이때 반환되는 문자열은 클래스 이름과 함께 구분자로 '@'가 사용되며, 그 뒤로 16진수 해시 코드(hash code)가 추가됩니다.
16진수 해시 코드 값은 인스턴스의 주소를 가리키는 값으로, 인스턴스마다 모두 다르게 반환됩니다.
+ 예제

```java
Car car01 = new Car();

Car car02 = new Car();

 

System.out.println(car01.toString());

System.out.println(car02.toString())
```
결과
```
Car@15db9742

Car@6d06d69c
```
### equals() 메소드
`equals()` 메소드는 해당 인스턴스를 매개변수로 전달받는 참조 변수와 비교하여, 그 결과를 반환합니다.
이때 참조 변수가 가리키는 값을 비교하므로, 서로 다른 두 객체는 언제나 false를 반환하게 됩니다.
```java
Car car01 = new Car();

Car car02 = new Car();

 

System.out.println(car01.equals(car02));

car01 = car02; // 두 참조 변수가 같은 주소를 가리킴.

System.out.println(car01.equals(car02));
```
결과
```
false   
true
```
### clone() 메소드
`clone()` 메소드는 해당 인스턴스를 복제하여, 새로운 인스턴스를 생성해 반환합니다.
하지만 Object 클래스의 clone() 메소드는 단지 필드의 값만을 복사하므로, 필드의 값이 배열이나 인스턴스면 제대로 복제할 수 없습니다.
```java
import java.util.*;
class Car implements Cloneable {
    private String modelName;
    private ArrayList<String> owners = new ArrayList<String>();
  
    public String getModelName() { return this.modelName; }                    // modelName의 값을 반환함

    public void setModelName(String modelName) { this.modelName = modelName; } // modelName의 값을 설정함

    public ArrayList getOwners() { return this.owners; }                      // owners의 값을 반환함

    public void setOwners(String ownerName) { this.owners.add(ownerName); }   // owners의 값을 추가함


    public Object clone() {
        try {
         Car clonedCar = (Car)super.clone();

         // clonedCar.owners = (ArrayList)owners.clone();

            return clonedCar;
      } catch (CloneNotSupportedException ex) {

            ex.printStackTrace();

            return null;

        }

    }

}

 

public class Object03 {

    public static void main(String[] args) {

      Car car01 = new Car();
     car01.setModelName("아반떼");
     car01.setOwners("홍길동");
     System.out.println("Car01 : " + car01.getModelName() + ", " + car01.getOwners() + "\n");

      Car car02 = (Car)car01.clone();
      car02.setOwners("이순신");
      System.out.println("Car01 : " + car01.getModelName() + ", " + car01.getOwners());
      System.out.println("Car02 : " + car02.getModelName() + ", " + car02.getOwners());
    }

}
```
결과
```
Car01 : 아반떼, [홍길동]

Car02 : 아반떼, [홍길동, 이순신]

Car02 : 아반떼, [홍길동, 이순신]
```