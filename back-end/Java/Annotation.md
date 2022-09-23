# 어노테이션(Annotation)
+ Java 5부터 추가된 기능

+ 클래스나 메소드 위에 붙여서 사용합니다(ex. @Override)

+ 소스코드에 메타코드(추가정보)를 주는 것

+ 설정된 값(어노테이션)을 통해 클래스나 메소드를 다르게 동작시킬 수 있다
커스텀 어노테이션 : 사용자가 직접 만들어서 정의하는 어노테이션

+ 대부분은 누군가가 만든 어노테이션을 쓴다. 하지만 이번 시간을 통해 어떤 식으로 어노테이션을 처리하는지 알아보자
### 1. 정의
 @를 이용한 주석, 자바코드에 주석을 달아 특별한 의미를 부여한 것


### 어노테이션 생성
+ 어노테이션을 JVM실행시에 감지할 수 있도록 하려면 @Retention(RetentionPolicy.RUNTIME)를 붙여줘야 합니다.
 ```java
 import java.lang.annotation.Retention;
import java.lang.annotation.RetentionPolicy;

@Retention(RetentionPolicy.RUNTIME)
public @interface Count100 {

}
```
### 어노테이션을 메소드에 적용
```java
public class MyHello {
    @Count100
    public void hello(){
        System.out.println("hello");
    }
}
```
### 어노테이션이 적용된  부분인지 체크하여 코드내에서 사용
```java
import java.lang.reflect.Method;
public class MyHelloExam {
    public static void main(String[] args) {
        MyHello hello = new MyHello();
        try{
            Method method = hello.getClass().getDeclaredMethod("hello");

            if(method.isAnnotationPresent(Count100.class)){
                for(int i=0;i<100;i++){
                    hello.hello();
                }
            }else{
                hello.hello();
            }
        } catch(Exception e){
            e.printStackTrace();
        }

    }
}
```