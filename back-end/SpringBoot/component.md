# Component
`Component`어노테이션의 경우 개발자가 직접 짠 클래스를 Bean으로 등록하기 위한 어노테이션이다.
```java
@Component
public class Student(){
    public Student(){
        System.out.println("hi);
    }
}
```
`Student`클래스는 개발자가 직접 짠 코드이다. 이러한 클래스를 Bean으로 사용하기 위해 상단의 `@Component`어노테이션을 사용하였다.

즉, 패키지 스캔 안에 이 어노테이션은 "이 클래스를 정의했으니 빈으로 등록하라" 는 뜻이 된다.

+ `Component`를 포함하는 다음 어노테이션도 스프링 빈으로 **자동** 등록된다.
    + `@Controller`
    + `@Service`
    + `@Repository`


### 등록 방법
1. application.xml 파일에 Bean을 직접 등록하는 것은 고전적인 방법이다.
```java
<?xml version="1.0" encoding="UTF-8"?>
<beans xmlns="http://www.springframework.org/schema/beans"
       xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
       xsi:schemaLocation="http://www.springframework.org/schema/beans http://www.springframework.org/schema/beans/spring-beans.xsd">
	
    // Bean을 등록하는 과정
    <bean id="bookService" class="com.ex.forblog.book.BookService">
        <property name="bookRepository" ref="bookRepository"/>
    </bean>
	
    // Bean을 의존성 주입(DI)하는 과정
    <bean id="bookRepository" class="com.ex.forblog.book.BookRepository"/>
</beans>
```

2. 최근에는 어노테이션으로 Bean을 등록한다.<br>
+ @Component, @Service, @Controller, @RestController, @Repository, @Bean, @Configuration 등 필요한 Bean을 등록할 수 있다. <br>

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbnbmLr%2Fbtq103g3rff%2FCJAOohdIWiBXVq28cU4Jyk%2Fimg.png)


 @Service, @Controller, @Repository어노테이션은 @Component어노테이션보다 조금 더 구체적인 어노테이션이다.
 

`Component`를 아무때나 사용할 수 있는 것도 아니다.
`@SpringBootApplication`어노테이션은 스프링의 가장 기본적인 설정을 해줍니다.
```java
Target(value = {ElementType.TYPE})
@Retention(value = RetentionPolicy.RUNTIME)
@Documented
@Inherited
@SpringBootConfiguration
@EnableAutoConfiguration
@ComponentScan(excludeFilters = {
    @ComponentScan.Filter(type = FilterType.CUSTOM, classes = {TypeExcludeFilter.class}),
    @ComponentScan.Filter(type = FilterType.CUSTOM, classes = {AutoConfigurationExcludeFilter.class})})
public @interface SpringBootApplication {

    @AliasFor(annotation = EnableAutoConfiguration.class)
    public Class<?>[] exclude() default {};

    @AliasFor(annotation = EnableAutoConfiguration.class)
    public String[] excludeName() default {};

    @AliasFor(annotation = ComponentScan.class, attribute = "basePackages")
    public String[] scanBasePackages() default {};

    @AliasFor(annotation = ComponentScan.class, attribute = "basePackageClasses")
    public Class<?>[] scanBasePackageClasses() default {};

    @AliasFor(annotation = ComponentScan.class, attribute = "nameGenerator")
    public Class<? extends BeanNameGenerator> nameGenerator() default BeanNameGenerator.class;

    @AliasFor(annotation = Configuration.class)
    public boolean proxyBeanMethods() default true;
}
```
여기서 `@ComponentScan`은 `@Component`어노테이션 및 `@Controller`, `@Service`, `@Repository`등의 어노테이션을 스캔하여 Bean에 등록합니다.

### ComponentScan
`@ComponentScan` 은 `@Component` 가 붙은 모든 클래스를 스프링 빈으로 등록한다.

이때 스프링 빈의 기본 이름은 클래스명을 사용하되 맨 앞글자만 소문자를 사용한다.<br>
+ 빈 이름 기본 : MemberServiceImpl 클래스의 빈이라면 자동으로 memberServiceImpl로 빈 이름이 지정된다.<br>
+ 빈 이름 직접 지정: 만약에 스프링 빈의 이름을 지정하고 싶다면 `@Component("spring")`
이런 식으로 지정하면 된다.

# Bean
개발자가 작성한 Method를 반환하는 객체를 Bean으로 만드는 것이다.
`@Configuration` 어노테이션이 들어간 Spring을 설정하는 클래스 내에 들어가는 메소드에서 선언한다.
```java
package hello.hellospring.controller;

import hello.hellospring.repository.MemberRepository;
import hello.hellospring.service.MemberService;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Controller;

@Controller
public class MemberController {
    private final MemberService memberService;

    @Autowired
    public MemberController(MemberService memberService){
        this.memberService = memberService;
    }
}

```
위와 같이 `@Bean`어노테이션에 `name`이라는 값을 이용하면 자신이 원하는 id로 `Bean`을 조정할 수 있다.

+ 위에 코드에서 생성자 위에 `@Autowired`라는 어노테이션이 있는데, 이 어노테이션을 사용하면 스프링이 관련된 객체를 스프링 컨테이너에서 찾아서 넣어준다.<br>
이렇게 의존성이 있는 객체를 넣어주는것을 의존성 주입(DI)라고 한다.

# 의존관계
+ 스프링 어노테이션을 사용한 컴포넌트 설정
    + 어노테이션의 역할
        + 컴파일러에게 코드 작성 에러에 대한 정보 제공
        + 실행 시 특별한 기능을 실행하도록 정보를 제공

    스프링에서 어노테이션을 붙이게 되면 어떻게 작동할까?
    스프링이 실행되는 순간 해당 어노테이션을 스프링이 인식하고, 해당 어노테이션에 있는 객체를 생성하여 스프링 컨테이너에 넣어둔다.

    각 클래스당 1개의 객체만 생성가능하다. 그러므로 같은 스프링 빈이면 인스턴스의 값이 같다.


    + `memberService()`는 서비스를 담당하기 때문에 `Service`어노테이션을 추가한다.
    ```java
    @Service
    public class memberService{
        ....
    } 
    ```

    + `MemoryMemberRepository`는 저장소의 역할을 하기 때문에
    `Repository`의 어노테이션을 추가한다.
    ```java
    @Repository
    public class MemoryMemberRepository implements MemberRepository{
        ....
    }
    ```
+ 스프링 빈 Configuration을 사용하는 방법
    어노테이션을 사용한 방법은 자동으로 스프링 빈에 등록하는 방법이었다면, `Configuration`은 내가 직접 수동으로 스프링빈에 등록하는 방법입니다.

    + SpringConfig클래스 생성
        ```java
        @Configuration
        public class SpringConfig{
            
            @Bean // Bean에 등록되어야한다는 객체라는 의미의 Annotation
            public memberService memberService(){
                return new memberService(memberRepository());
                // 아래에서 생성된 memberRepository 객체를 넣어줌. 
            }
            @Bean
            // 여기서 MemberRepsitory는 인터페이스, MemoryMemberRepsitory로 구현하기 위해서 객체로 가져옴
            public MemberRepository memberRepository(){
                return new MemoryMemberRepository();
            }
        }
        ```