# IOC컨베이너
스프링객체를 생성하고 관리하고 책임지고 의존성을 관리해주는 컨테이너가 있는데, 그것이 IOC컨베이너 입니다.<br>
인스턴스가 생성하고 소멸하는 것을 개발자 대신에 관리해준다.
+ IOC는 객체를 관리해준다.
+ POJO의 생성,초기화,서비스의 권한을 가진다.
+ 개발자가 해도 되지만 개발자는 컨베이너에게 맡긴다.
+ TDD의 용이하다.

### 분류
+ DL(Dependency Lookup)
    +  저장소에 저장되어 있는 Bean에 접근하기 위해 컨테이너가 제공하는 API를 이용하여 Bean을 Lockup하는 것
+ DI(Dependency Injection) : DI란 외부에서 객체를 생성하여 클라이언트로 전달하여 의존 관계를 연결시키는 것
    + 각 클래스에 Bean정보를 바탕으로 컨베이너가 자동으로 연결시켜주는 것
        + 생성자 
        + 필드
        + 수정자

    ![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fx4WUU%2Fbtq9gXndYek%2FCwB8xqIdfQh1ox2P9H6bV1%2Fimg.png)

    스프링 컨테이너가 관리하는 객체를 빈(Bean)이라고 하고, 빈(Bean)을 관리하는 컨테이너를 빈 팩토리(BeanFactory)라고 한다.

    ### BeanFactory
    컨테이너에서 객체를 생성하고 DI를 처리한다.<br>
    + Bean을 등록/생성/초기화/관리 한다.
    + Bean을 조회할 수 있는 getBean() 메소드가 있다.