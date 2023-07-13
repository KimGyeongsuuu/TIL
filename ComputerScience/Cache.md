# Cache(캐시)란?
## 1. 캐시란?
Cache란 자주 사용하는 값이나 데이터를 미리 복사해 놓는 임시 저장소를 가리킨다.
아래의 계층과 같이 Cache는 저장공간이 작고 비용이 비싼대신 빠른 성능을 제공한다.

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FZdW35%2FbtqCbTDmFj5%2FAKbAUKiWseStnfD1Cd7gqk%2Fimg.png)

## 2. Cache-Control
브라우저가 캐시를 하기 위해서는 응답 헤더에 Cache-Control이라는 헤더가 있어야한다. 이 헤더를 통해 얼마나 캐시를 저장하고 어떻게 적용할지 정한다.

+ `no-store` : 캐시 사용 안함
+ `no-cache` : 캐시를 사용하기 전에 사용해도 되는지 체크하는 옵션
+ `public` : 모든 환경에서 사용가능
+ `private` : 브라우저 환경에서만 사용가능
+ `max-age` : 캐시의 유효 시간(초 단위)

![img](https://blog.kakaocdn.net/dn/nd3WM/btqyzcuzmUG/hjCOC25nWDkCN6SI4OEZp0/img.png)

위와 같은 흐름으로 흘러간다.

## 3. Local Cache vs Global Cache

### [Local Cache]
+ Local 장비 내에서만 사용되는 캐시로, Local 장비의 Resource를 이용한다.
+ Local에서만 작동하기 때문에 속도가 매우빠르다.
+ Local에서만 작동되기 때문에 다른 서버와 데이터 공유하기가 어렵다.

### [Global Cache]
+ 여러 서버에서 Global Cache에 접근하여 사용하는 캐시로 분산된 서버에서 데이터를 조회하고 저장할 수 있다.
+ 네트워크를 통해 데이터를 가져오므로, Local Cache에 비해 느리다.
+ 다른 서버간의 데이터 공유가 쉽다.

