# 어노테이션(Annotation)
### 1. 정의
 @를 이용한 주석, 자바코드에 주석을 달아 특별한 의미를 부여한 것


### 어노테이션 생성
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