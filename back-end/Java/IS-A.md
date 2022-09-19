# IS-A
### 상속이란
자바에는 부모클래스의 기능을 자식클래스가 물려받을 수 있는 기능이 있다.<br>
그것이 상속이다!!!
```java
class Animal {  
    String name;

    void setName(String name) {
        this.name = name;
    }
}

class Dog extends Animal {
}

public class Sample {
    public static void main(String[] args) {
        Dog dog = new Dog();
        dog.setName("poppy");
        System.out.println(dog.name);  // poppy 출력
    }
}
```
클래스를 상속하려면 `extends`를 사용해야한다.<br>
아래의 코드는 Dog라는 클래스를 Animal이라는 클래스로 부터 상속받는다는 의미이다.
```java
class Dog extends Animal{
    ...
}
```

### IS-A 관계
Dog 클래스는 Animal 클래스를 상속했다. 즉, Dog는 Animal의 하위 개념이라고 할 수 있다. 이런 경우 Dog는 Animal에 포함되기 때문에 "개는 동물이다"라고 표현할 수 있다.

자바는 이러한 관계를 IS-A 관계라고 표현한다. 즉 "Dog `is a` Animal" 과 같이 말할 수 있는 관계를 IS-A 관계라고 한다. 이렇게 IS-A 관계(상속관계)에 있을 때 자식 클래스의 객체는 부모 클래스의 자료형인 것처럼 사용할 수 있다.

즉, 다음과 같은 코딩이 가능하다.
```java
Animal dog = new Dog();  // Dog is a Animal
```
+ 다만 여기서 한 가지 주의해야 할 점이 있다. Dog객체를 Animal 자료형으로 사용할 경우에는 Dog 클래스에만 존재하는 sleep 메소드를 사용할 수 없다는 점이다. 이런 경우에는 Animal 클래스에 구현된 setName 메소드만 사용이 가능하다.
```JAVA
Dog dog = new Animal();  // 컴파일 오류: 부모 클래스로 만든 객체는 자식 클래스의 자료형으로 사용할 수 없다.
``` 
```java
Animal dog = new Dog();  // Dog is a Animal (O)
```
+ 위 코드를 읽어보면 "개로 만든 객체는 동물 자료형이다."라고 읽을 수 있다.

```java
Dog dog = new Animal();  // Animal is a Dog (X)
```
+ 위 코드를 읽어보면 "동물로 만든 객체는 개 자료형이다."라고 읽을 수 있다.
동물로 만든 객체는 "개"말고도 "호랑이", "고양이"도 있을 수 있기 때문이다.