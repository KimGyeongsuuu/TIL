# 싱글톤(Singleton)
자바에서 프로그램이 동작할 때 최초 한번만 메모리를 할당하고 할당된 메모리에서만 사용하는것을 말한다.
단순하게 말하면 객체의 인스턴스가 오직 하나만 생성되는 것을 말한다.

자바에서 객체를 생성할 때 new를 사용해서 객체를 만드는데, 싱글톤을 사용하면 기본 생성자를 private로 하여서 new연산자로 만들지 못하게 한다.

```java
public class Singleton {

    private static Singleton instance = new Singleton();
    
    private Singleton() {
        // 생성자는 외부에서 호출못하게 private 으로 지정해야 한다.
    }

    public static Singleton getInstance() {
        return instance;
    }

    public void say() {
        System.out.println("hi, there");
    }
}
```

### 사용하는 이유
+ 가장 좋은 이점은 메모리 측면이다. 최초의 new 연산자를 사용하여 객체를 한 번만 생성하니 메모리 낭비를 방지할 수 있다. 그리고 이미 만들어진 객체를 사용하니 빠르게 사용할 수 있다.
+ 또 다른 장점은 데이터 공유가 쉽다는 것이다. 싱글톤 데이터는 전역으로 사용되기 때문에 인스턴스들이 접근하여서 사용할 수 있다는 것이다.


