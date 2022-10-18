# Spring Container
`Container`는 스프링에서 가장 중요한 것이다. `Container`는 개발자 대신에 Bean을 생성하고, 관리하고, 제어하는 역할을 한다.
그래서 개발자는 `@어노테이션`만 제공하면 Container가 알아서 개발자가 원하는 상황에 코드를 실행합니다.

ApplicationContext 를 스프링 컨테이너라고 한다.
스프링 컨테이너는 파라미터로 넘어온 설정 클래스 정보를 사용해서 스프링 빈을 등록한다.
|이름|설명|
|---|---|
|IOC(Inversion of Control)|개발자는 New 연산자, 인터페이스 호출, 팩토리 호출방식으로 객체를 생성하고 소멸시킨다.|
|DI(Dependency Injection)|IoC를 실제로 구현하는 방법으로서 의존성있는 컴포넌트들 간의 관계를 개발자가 직접 코드로 명시하지 않고 컨테이너인 Spring이 런타임에 찾아서 연결해주게 하는 것|

### 종류
+ 빈팩토리 BeanFactory
    + Bean을 등록하고 생성하고 조회하고 돌려준다.
```java
BeanFactory factory = new XmlBeanFactory(new FileInputStream("bean.xml"));

MyBean myBean = (Mybean) factory.getBean("myBean");
```

+ 어플리케이션 컨텍스트 Application Context
    + 빈 팩토리를 상속한, 빈 팩토리를 확장한 향상 된 컨테이너
    + 기본적인 기능은 빈 팩토리와 동일하고 스프링이 제공하는 부가 서비스를 제공
```java
ApplicationContext context = new ClassPathXmlApplicationContext("conf/bean.xml");

MyBean bean = context.getBean("myBean");
```

### 두가지의 차이점
+ 빈 팩토리
    + 처음으로 getBean()이 호출된 시점에서야 해당 빈을 생성
+ 애플리케이션 컨텍스트
    + 국제화 지원 텍스트 메시지 관리
    + 이미지 파일 로드
    + 리스너로 등록된 빈에게 이벤트 발생 통보