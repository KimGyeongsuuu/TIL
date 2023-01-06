# ComputerScience
### 프로그램
어떤 작업을 하기 위해 실행되는 파일 또는 프로그램

### 프로세스
메모리에서 현재 실행되고 있는 프로그램을 말한다.

### 스레드
프로세스 내에 하나의 실행 단위를 말한다. 프로세스내에서는 프로세스를 서로 공유할 수 있으며, 하나에 프로세스에서 다수의 스레드를 실행단위로 구분하는것을 **멀티스레드**라고 구분합니다.

![thread](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbYxB0K%2Fbtrh4pH7qiV%2F9EL0YsPlvAWEFkRVcRn0y0%2Fimg.png)
+ 하나의 프로세스가 생성되면 자동으로 메인 스레드가 생성이 된다
+ 하나의 프로세스는 여러개의 스레드를 가질 수 있다.
+ 스레드는 프로세스 내에서 Stack만 할당받고 나머지 Code,Data,Heap영역은 공유한다.

멀티스레드를 쓰는 이유는 멀티프로세스보다 공유하는 통신비용이 덜 들고 할당되는 시스템콜이 감소할 수 있기 때문에 훨씬 효율적이다.

**멀티 프로세스**<br>
하나의 프로그램을 여러개의 프로세스로 구성하여 각 프로세스가 하나의 작업을 처리하는 것을 말한다.
+ 장점 : 하나의 프로세스에서 문제가 생겨도 프로그램이 돌아간다
+ 단점 : context switching 문제 발생

**멀티 스레드**<br>
하나의 프로그램을 여러개의 스레드로 구성하고 각 스레드에서 하나의 작업을 처리하는 것을 말한다. <br>
하나의 스레드 오류로 전체 프로세스 문제가 생긴다.
+ 장점 : 시스템의 자원 처리 감소, 실행 속도 향상
+ 단점 : 디버깅이 어렵다

**멀티 스레드를 사용하는 이유**

자원을 효율성 증대, 처리 비용 감소, 응답 시간 단축<br>
프로세스 생성 시 자원을 할당하는 시스템 콜이 줄어들어 자원 소모가 적고 자원을 효율적으로 관리할 수 있습니다. 


**스레드 Safe란**<br>

여러개의 스레드가 동시에 실행이 되도 안전하다는 뜻이다.


### 동기화
공유된 자원에 여러 프로세스/스레드가 동시에 접근하면 `Critical section` 문제가 발생하여 원하는 결과가 나오지 않을 수 있기 때문에 한 번에는 하나의 프로세스만 접근할 수 있도록 제한을 둬야 합니다

### DeadLock(교착상태)
프로세스가 자원을 얻지 못하여 다음 프로세스를 실행을 못하는 상태.<br>
한정된 자원보다 많은것을 사용하려고 할 때 발생됩니다.

교착상태의 조건
+ 상호배제 : 필요한 자원에 대해 배타적 통제권 요구
+ 점유대기 : 할당된 자원을 가진 상태에서 다른 자원을 기다림
+ 비선점 :  어떤 자원이 사용이 끝날때까지 다른 자원을 뺏어올 수 없다.
+ 순환대기 : 순차적으로 다음 프로세스가 요구하는 자원을 가지고 있음.

### RESTful API
http메서드를 통해 자원을 처리하는 방식이다.
+ 리소스와 행위를 명사적이고 직관적으로 분리
+ 행위는 http method get,post,put,patch,delete로 표현한다.
+ Header와 Body를 완전히 분리
    + Entity의 내용은 Body를 통하여 요청
+ API 버전관리

장점
+ 기존의 http 인프라를 그대로 사용할 수 있다.

단점
+ http메서드가 4개 밖에 없다.
+ http 통신 프로토콜에 대해서만 지원한다.


### HTTP Protocol
서버와 클라이언트가 데이터를 주고받기 위한 프로토콜이다.

응답코드
+ 1XX : 정보 확인
+ 2XX : 성공
    + 200 : 서버 요청 처리 성공
    + 201: 요청 접수 후 새 리소스 작성
+ 3XX : 리다이렉트
    + 301: 요청 페이지가 새 위치로 영구적 이동 (요청페이지 변경)
    + 302: 임시이동 요청자
+ 4XX : 클라이언트 오류
    + 400: 클라이언트 오류 (잘못된 클라이언트 요청)
    + 401: 권한 없음
    + 404: 서버에 요청한 리소스 찾을 수 없음
+ 5XX : 서버측 오류

### HTTP/HTTPS
http와 https의 차이점은 https는 http를 통신하느 소켓 부분을 SSL이라는 프로토콜로 대체한다.

+ HTTP동작순서 : TCP -> HTTP
+ HTTPS동작순서 : TCP -> SSL -> HTTP

SSL을 사용하지 않으면 암호화로 인해 속도 저하가 일어날 수 있다.

### SSL
Secure Socket Layer이라는 뜻으로 보완프르토콜을 통해 클라이언트와 서버가 통신하는것을 말합니다.
SSL을 사용하면 모든 데이터가 비공개로 전송됩니다.
SSL암호화를 사용해서 데이터 변조를 막습니다.

### 웹 통신의 흐름
1. 브라우저가 url을 입력한다.
2. 브라우저는 DNS 서버로 가서 웹사이트의 IP주소를 찾는다.
3. 브라우저는 서버에게 웹사이트의 사본을 보내달라는 **http요청 메세지**를 서버로 전송한다.
4. 브라우저의 요청을 받은 서버는 메세지를 클라이언트로 전송한다.
5. 서버는 응답할 파일들을 데이터 패킷이라는 곳에 저장하여서 작은 덩어리로 클라이언트로 전송한다.
6. 브라우저는 서버로부터 응답받은 데이터패킷을 조립해서 사용자에게 웹사이트를 보여준다.


### 쿠키
클라이언트에 저장된느 Key:Value값입니다. 유효시간 명시가 가능하며 주로 활용되는 곳은 자동로그인,장바구니,아이디 자동저장 입니다

### 세션
쿠키가 클라이언트에 저장된다면 세션은 서버에 데이터가 저장되는 것을 말합니다. 클라이언트가 http요청을 하면 서버엔진이 자동으로 유일한 id를 부여하는데 이것이 세션id입니다.<br>
브라우저를 종료시키면 자동으로 세션이 종료됨으로 보안은 좋지만 사용자가 많아지면 서버 메모리에 있어서 비표율적이다. 그렇기에 성능저하 문제가 발생할 수 있다.

**사용하는 이유**<br>

정보가 유지되지 않으면 사용자 입장에서 다른 페이지 한 번 갈때마다 계속 로그인과 인증을 해야하는 상황이 오기때문에 상태유지가 필요한 상황에서는 쿠키와 세션을 꼭 사용해야한다.


**쿠키 동작 순서**<br>
1. 클라이언트 페이지의 요청
2. 웹서버가 쿠키를 생성
3. 클라이언트에게 http응답을 할 때 생성된 쿠키도 함께 전송한다.
4. 서버에서 클라이언트로 전송한 쿠키를 클라이언트에 저장
5. 클라이언트가 재접속을 할때 쿠키를 서버로 전송해서 정보를 유지시킨다.


**세션 동작 순서**<br>
1. 클라이언트 페이지의 요청
2. 서버는 클라이언트가 보낸 쿠키를 확인하고 클라이언트가 세션id를 전송했는지 확인
3. 세션id가 존재하지 않으면 세션id를 생성하고 클라이언트로 전송
4. 서버에서 클라이언트로 보내준 세션id를 활용하여서 서버에 저장
5. 클라이언트는 재접속시 쿠키를 이용해서 세션id를 서버로 전달

### stack
먼저들어온값이 가장 나중에 나가는 LIFO(Last In First Out)형식의 자료구조이다.<br>
+ pop : 가장 최근에 들어간 값을 삭제한다
+ push : 값을 삽입한다
+ top : 가장 최근의 값을 리턴한다.


### queue
큐는 가장 먼저 들어간 값이 가장 먼저 나가는 FIFO(First In First Out)형식의 자료구조이다.<br>


### OSI 참조모델
통신할 때 어떻게 메세지를 주고 받고 어떤 언어를 사용할 지 정하는 규칙, 이러한 규칙을 프로토콜이라고 한다.

![OSI](OSI.png)

**물리계층**
+ 데이터를 주고받는 기능을 수행

**데이터링크계층**
+ 물리계층으로 전송되는 정보를 안전하게 관리하는 기능을 수행
+ MAC 주소를 기반

**네트워크계층**
+ Router, IP
+ 데이터를 목적지까지 안전하고 빠르게 전송가능
+ IP주소를 지정하고 패킷데이터를 전송

**전송 계층**
+ TCP / UDP
+ 위 프로토콜을 통해 통신 활성화, 전송 역할

**세션 계층**
+ API, SOCKET
+ 데이터가 연결하기 위한 논리적 연결을 담당
+ TCP/IP 세션을 생성하고 삭제하는 역할

**표현 계층**
+ JPG, MPEG
+ 데이터 표현에 대한 인터페이스 제공

**응용 계층**
+ HTTP,DNS,FTP


### WAS와 Web Server의 차이

**Web Server**

웹 브라우저에서 특정 페이지를 요청할 때 서버에서 요청을 받아 정적 콘테츠를 제공하는 웹서버를 말한다. 웹서버는 동적콘텐츠뿐만 아니라 동적콘텐츠를 받으면 WAS에 해당 데이터를 전송합니다. 그리고 WAS를 다시 사용자에게 전송하는 다리역할도 할 수 있습니다.

**WAS**

WAS는 웹서버가 단독적으로 처리 할 수 없는 DB나 관련로직이 필요한 동적콘텐츠를 제공합니다. 현재는 WAS가 가진 웹서버에서도 정적콘텐츠를 처리하는데 있어서 성능상에 큰 문제는 없습니다.

**필요한 이유**
웹페이지는 동적,정적 콘텐츠를 모두 제공합니다. 동적콘텐츠는 사용자 목적에 맞게 제공해야 합니다. 


### DNS
인터넷 표준 프로토콜은 TCP/IP입니다. 이 프로토콜을 사용하는 네트워크 안에서 host를 식별하기 위한 목적으로 IP주소를 사용합니다. 길게 숫자로 이루어진 IP 주소를 사람이 읽기 편한 주소 이름으로 변환한 것을 말합니다. 대표적으로 DNS 서비스는 aws의 route 53이 해당됩니다.



### Logging Level
Logging Level은 크게 4가지로 나뉜다.
+ ERROR
    
    에러 로그는, 프로그램 동작에 큰 문제가 생겼다는 의미이다. 즉시 문제를 해결해야하는 상황이라는 뜻이다.
    (DB를 사용할 수 없는 상황, 중요한 에러가 나오는 상황)

+ WARN
    
    주의해야하지만, 프로세스는 계속 진행되는 상태
    + 명확한 문제 : 현재 데이터를 사용불가
    + 잠재적 문제 : 개발 모드로 프로그램 실행

+ INFO

    중요한 비즈니스 프로세스가 시작될 때와 종료될 때를 알려주는 로그


+ DEBUG

    개발자가 기록할 가치가 있는 정보를 남기기 위해 사용하는 레벨


### [TCP] 3 way handshake & 4 way handshake

TCP는 정확한 전송을 보장해야 한다. 따라서 통신하기에 앞서, 논리적인 접속을 성립하기 위해 3 way handshake 과정을 진행한다.

#### 3 way handshake - 연결 

![img](https://camo.githubusercontent.com/4acea6af95884347810f057d00c6c4643a56d4a7dbbdf49740745560cd45cc1f/68747470733a2f2f6d656469612e6765656b73666f726765656b732e6f72672f77702d636f6e74656e742f75706c6f6164732f5443502d636f6e6e656374696f6e2d312e706e67)


1. 클라이언트가 서버에게 SYN 패킷을 보냄
2. 서버가 SYN패킷을 받고, 그것을 받았다는 신호로 ACK와(x+1) SYN패킷을 보냄
3. 클라이언트는 ACK와 SYN패킷을 받고 ACK(y+1)을 서버로 보냄

이런식으로 3번의 통신이 완료되면 연결이 성립된다.<br>
이것을 `3 way handshake`라고 말한다.



#### 4 way handshake - 연결 해제

클라이언트와 서버간의 연결이 끝나면 연결을 해제해야 한다.

![img](https://camo.githubusercontent.com/8bb8960e46a3bfada6a237a7a91bce75a0a3e0e34eab5c1f5143ca6fe34d0b5f/68747470733a2f2f6d656469612e6765656b73666f726765656b732e6f72672f77702d636f6e74656e742f75706c6f6164732f434e2e706e67)

1. 클라이언트는 서버와의 연결을 종료시키겠다는 FIN플래그를 보낸다.
2. 서버는 FIN을 받고 확인했다는 ACK를 클라이언트에게 보낸다.
3. ACK를 모두 보냈다는 FIN을 클라이언트에게 보낸다.
4. 클라이언트는 FIN을 받았다는 ACK를 서버에게 보낸다.

+ 서버는 ACK를 받고 서버를 종료한다.
+  TIME_WAIT 시간이 끝나면 클라이언트도 닫는다.

이런식으로 4번의 통신이 완료되면 연결이 해제된다.<br>
이것을 `4 way handshake`라고 말한다.


### CSR & SSR

```
CSR : Client Side Rendering
SSR : Server Side Rendering
```

**CSR 장단점**
+ 장점
    + 트래픽 감소
        
        필요한 데이터만 받는다

    + 사용자 경험

        새로고침이 발생하지 않음. 사용자가 네이티브 앱과 같은 경험을 할 수 있음.

+ 단점
    + 검색 엔진

        크롬에서 리액트로 만든 웹앱 소스를 확인하면 내용이 비어있음. 이처럼 검색엔진 크롤러가 데이터 수집에 어려움이 있을 가능성 존재
