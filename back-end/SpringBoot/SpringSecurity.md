# SpringSecurity
Spring 기반의 애플리케이션 보안(인증과 권한, 인가)을 담당하는 스프링 하위 프레임워크이다<br>
SpringSecurity는 `인증`과 `권한`에 대한 작업을 `Filter`의 흐름에 따라 처리한다.<br>
Filter이기에 Dispatcher Servlet으로 가기전에 해당한다.

SpringSecurity는 보안에 관련된 작업을 처리해주기 때문에 개발자는 보안과 관련된 로직을 일일이 작성하지 않아도 된다.

<hr>

## 인증(Authorization)과 인가(Authentication)

+ 인증(Authorization) : 해당 사용자가 본인이 맞는지 **인증**
+ 인가(Authentication) : 인증된 사용자가 요청한 자원에 대한 **권한**이 있는지 결정

SpringSecurity에서는 인증 절차를 거친 후 인가 절차를 거친다. 인가를 통해 사용자가 인증이 되면 그 사용자의 권한을 결정하는 것이다.

SpringSecurity는 `Principal`,`Credential`을 사용하여 Credential 기반의 인증을 한다.
+ Principal : 보호받는 리소스에 접근하는 대상
+ Credebtial : 리소스에 접근하는 대상의 비밀번호

<hr>

## SpringSecurity 주요 모듈

![springsecurity](https://velog.velcdn.com/images%2Fjsj3282%2Fpost%2F27a42080-ad39-48e5-8c66-c6fef7f1e598%2F%E1%84%83%E1%85%A1%E1%84%8B%E1%85%AE%E1%86%AB%E1%84%85%E1%85%A9%E1%84%83%E1%85%B3.png)

### SecurityContextHolder
보안 주체의 세부 정보를 포함하여 응용 프로그램의 현재 보안 컨텍스트에 대한 세부 정보가 저장된다. SecurityContext의 전략은 3가지의 기본 전력이 있다.

+ SecurityContextHolder.MODE_THREADLOCAL: `ThreadLocalSecurityContextHolderStragegy` 클래스를 구현체로 사용하며, ThreadLocal을 사용하여 SecurityContext를 공유한다. ThrealLocal은 같은 쓰레드 내에서 공유할 수 있는 자원을 의미한다. defualt 모드이다.
+ SecurityContextHolder.MODE_INHERITABLETHREADLOCAL: `InheritableThreadLocalSecurityContextHolderStrategy` 클래스를 구현체로 사용하며, inheritableThreadLocal을 사용하여 SecurityContext를 공유한다. 자식 쓰레드까지 공유할 수 있는 자원을 의미한다.
+ SecurityContextHolder.MODE_GLOBAL: `GlobalSecurityContextHolderStrategy` 클래스를 구현체로 사용하며, static 선언하여 SecurityContext를 저장한다. 해당 JVM 내의 인스턴스들은 모두 공유할 수 있다.


### SecurityContext
Authentication을 보관하는 역할이다. `SecurityContext`를 통해 Authentication객체를 꺼내올 수 있다.

### Authentication
Authentication은 현재 접근하고 있는 주체의 정보와 권한을 담는 인터페이스이다. SecurityContext에 저장되며 SecurityContext에서 꺼내올 수 있다.

```java
public interface Authentication extends Principal, Serializable {


    // 현재 사용자의 권한 목록을 가져온다.
    Collection<? extends GrantedAuthority> getAuthorities();

    // credials를 가져온다.
    Object getCredentials();

    // 인증 요청에 대한 추사 세부 정보를 가져온다.
    Object getDetails();

    // 인증되는 주체의 id를 가져온다.
    Object getPrincipal();

    // 인증 여부를 가져온다.
    boolean isAuthenticated();

    // 인증 여부를 설정한다.
    void setAuthenticated(boolean isAuthenticated) throws IllegalArgumentException;

}
```
### UsernamePasswordAuthenticationToken

UsernamePasswordAuthenticationToken은 Authentication을 구현한 AbstractAuthenticationToken의 하위 클래스이다. User의 id가 Principal의 역할을 하고 Password가 Credential의 역할을 한다.


### AuthenticationProvider
AuthenticationProvider에서는 실제 인증 부분을 처리한다. 인증 전에 Authentication 객체를 받아서 인증이 완료된 Authentication을 반환한다.

```java
public interface AuthenticationProvider {

    // 인증 전의 Authentication 객체를 받아 인증된 Authenticaiton 객체를 반환한다.
    Authentication authenticate(Authentication authentication) throws AuthenticationException;

    // Authentication 객체를 지원 하는지 여부를 반환한다.
    boolean supports(Class<?> authentication);
}
```

### Authentication Manager

Authentication Manager를 통해 인증을 처리한다. Authentication Manager에 등록된 Authentication Provider를 통해 인증이 처리된다. 인증에 성공하게 되면 SecurityContext에 등록이 될것이다. 그리고 인증 상태를 유지시키기 위해서는 Session에 저장(Spring Security는 기본적으로 세션에 기반하여 동작한다) 인증에 실패하게 되면 AuthenticaitonException예외를 던진다. 실제 인증 로직은 AuthenticationManager의 구현체인 ProviderManager에 들어있다.


### UserDetails
인증에 성공하게 되면 UserDetails객체는 Authentication을 구현한 UsernamePasswordAuthenticationToken을 생성하기 위해 사용된다.

```java
public interface UserDetails extends Serializable {

    // 사용자에게 부여된 권한을 반환한다.
    Collection<? extends GrantedAuthority> getAuthorities();

    // 사용자를 인증하는데 사용된 암호를 반환한다.
    String getPassword();

```