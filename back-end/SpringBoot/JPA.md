# JPA
+ 자바 ORM 기술에 대한 API 표준 명세. (ORM을 사용하기 위한 인터페이스의 모음)
## ORM이란
+ 자바에서 객체가 DB테이블이 되도록 매핑시켜주는 프레임워크
+ SQL을 자동으로 생성
+ 데이터베이스를 편하게 사용할 수 있다.

|SQL Mapper|ORM|
|--|--|
|자바 클래스와 SQL문을 매핑|자바 클래스와 DB를 매핑|
|SQL를 명시하여 직접 생성|자동으로 생성|
|필드를 매핑하는 것이 목적|RDB의 관계를 Object에 반영하는 것이 목적|
|myBatis, jdbcTemplate|JPA, Hibernate|

### SQL의 문제


### JPA의 동작

![img](https://ultrakain.gitbooks.io/jpa/content/chapter1/images/JPA.png)
JPA는 애플리케이션과 JDBC사이에서 동작합니다.<br>
개발자가 JPA를 사용하면, JPA내부에서 JDBC의 API를 사용하여서 SQL를 호출하고, DB와 통신한다.


### 사용하는 이유
+ SQL 중심적인 개발에서 객체 중심의 개발이 가능하다.
+ INSERT SQL을 작성하고 JDBC API를 사용하는 지루한 작업들을 JPA가 알아서 작업해준다.
+ CREATE TABLE같은 DDL문 자동 작성
+ 엔티티에 필드 추가시 등록, 수정, 조회 관련 코드를 모두 변경해야한다.
하지만 JPA를 사용하면 이런 과정을 JPA가 대신 처리해주기 때문에 개발자가 직접 변경할 필요가 없으니 유지보수 하기에도 편리하다
+ 패러다임의 불일치 해결

### 장점
+ SQL문을 직접 작성하지 않기 때문에 개발자는 비즈니스 로직을 구성하는데 집중할 수 있다.
+ 객체지향적인 코드를 작성할 수 있다.
+ 유지보수의 유의하다.
### 단점
+ 프로젝트의 규모가 크고 복잡하여 설계과정에서 문제가 발생하여 원하지 않은 Query문이 자동생성되어서 성능이 저하될 수 있다.



### ddl-auto 옵션 종류
+ create : 기존테이블 삭제 후 다시 생성(DROP + CREATE)
+ create-drop : create와 같지만 종료시점에 테이블을 drop을 한다
+ update : 변경된 부분만 적용
+ validate : 엔티티와 테이블이 정상 매팽되는지 확인
+ none : 사용하지 않겠다

**주의**
+ 운영장비에서는 `create`, `create-drop`, `update`는 사용하면 안된다.
+ 개발 초기에는 `create`, `update`를 사용한다.
+ 테스트 단계에서는 `update`, `validate`를 사용한다.
+ 운영 단계에서는 `validate`, `none`을 사용한다.

