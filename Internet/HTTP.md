# HTTP
### HTTP란?
+ Hyper Text Transfer Protocaol의 두문자어로, **인터넷에서 데이터를 주고받을 수 있는 프로토콜**입니다. 프로토콜은 규칙이라고 생각하면 된다. 규칙이 있기 때문에, 모든 프로그램이 이 규칙에 맞춰 개발해서 서로 정보를 교환할 수 있게 된 것이죠.

### 동작
+ 클라이언트 즉, 사용자가 브라우저를 통해서 어떠한 서비스를 url을 통하거나 다른 것을 통해서 **요청**을 하면 서버에서는 해당 요청사항에 맞는 결과를 찾아서 사용자에게 **응답**을 하는 형태로 동작한다.
    + 요청 : client -> server
    + 응답 : server -> cilent

### 특징
+ HTTP 메시지는 **HTTP서버**와 **HTTP클라이언트**에 의해 해석이 된다.
    + 이렇게 서버와 클라이언트가 분리된 네트워크 환경에서,  
    클라이언트는 서버로 요청 **Request**을 전송하고, 서버는 요청에 대한 응답 **Response**을 함으로써 통신하게 되는 것입니다.

    ![http](https://postfiles.pstatic.net/MjAyMTA0MDdfMTE4/MDAxNjE3NzgxMDA2MTE1.ZuJZfgIFE5wa37-7TzgzUW5AF5Q8bxmuYotnDRnIfHcg.mQtDEHb9Pr98nuOB5ROIlOtWb80O10pA708TeYonp1Mg.PNG.aservmz/image.png?type=w966)
+ HTTP는 연결 상태를 유지하지 않는 비연결성 프로토콜이다.
+ HTTP는 비연결성 프로토콜이기 때문에 요청/응답 방식으로 동작한다.

![HTTP](https://velog.velcdn.com/post-images%2Fsurim014%2Fe0aa5520-2d59-11ea-86da-fb3b00230640%2Fimage.png)

### Request (요청)
+ 클라이언트가 서버에게 연락하는 것을 요청이라고 하며 요청을 보낼때는 요청에 대한 정보를 담아서 서버로 보낸다.

### 예시
+ 서버는 주문서를 받아 클라이언트가 무엇을 요청했는지 알 수 있다. 이처럼 요청은 식당에서 주문서를 작성하는 것 이라고 생각하면 된다.

### 종류
+ GET : 자료를 **요청**할 때 사용
+ POST : 자료를 **생성**할 때 사용
+ PUT : 자료의 **수정**을 요청할 때 사용
+ DELETE : 자료의 **삭제**를 요청할 때 사용

### Reqeust HTTP 메시지 예시
```
GET https://velog.io/@surim014 HTTP/1.1  // 시작줄
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) ...  // 헤더
Upgrade-Insecure-Reqeusts: 1
```
1. 시작줄(첫 줄)
+ 매서드 구조 버전으로 구성
    + GET : HTTP Method
    + http://velog.io/@surim014 : 사이트 주소
    + HTTP/1.1 : HTTP 버전

2. 헤더 (두 번째 줄부터)
+ **요청**에 대한 정보를 담고 있다. User-Agent, Upgrade-Insecure-Requests 등등이 헤더에 해당되며 헤더의 종류는 매우 많다.

3. 본문 (헤더에서 한 줄 띄고)
+ **요청을 할 때 함께 보낼 데이터를 담는 부분**이다.

### Response (응답)
+ **서버가 요청에 대한 답변을 클라이언트에게 보내는 것**을 응답이라고 한다.
### Status Code (상태 코드)
+ **1XX (조건부 응답)** : 요청을 받았으면 작업을 계속한다.
+ **2XX (성공)** : 클라이언트가 요청한 동작을 수신하여 이해했고 승난했으며 성곡적으로 처리했음을 가리킨다.
+ **3XX (리다이렉션 완료)** : 클라이언트는 요청을 마치기 위해 추가 동작을 취해야 한다.
+ **4XX (요청 오류)** : 클라이언트에 오류가 있음을 나타낸다.
+ **5XX (서버 오류)** : 서버가 유효한 요청을 명백하게 수행하지 못했음을 나타낸다.

### Resonse HTTP 메시지 예시
```
HTTP/1.1 200 OK														// 시작줄
Connection: keep-alive												 // 헤더
Content-Encoding: gzip												 
Content-Length: 35653
Content-Type: text/html;

<!DOCTYPE html><html lang="ko" data-reactroot=""><head><title...
```
1. 시작줄 (첫 줄)
+ 첫 줄은 버전 상태코드 상태메시지로 구성되어 있다. 200은 성공적인 요청이었다는 뜻이다.
2. 헤더 (두 번째 줄부터)
+ 두 번째 줄부터는 헤더로 응답에 대한 정보를 담고 있다.
3. 본문 (헤더 뒤부터)
+ 응답 메시지에는 요청한 데이터를 담아서 보내주기 때문이다. 응답 메시지에 HTML이 담겨 있는데 이 HTML을 받아 브라우저가 화면에 렌더링한다.

# HTTP HTTPS차이
HTTPS는 SSL인증서를 사용하는 HTTP입니다. SSL인증서는 일반적인 요청을 암호화해서 합니다.
HTTPS는 보안용 프로토콜입니다.

### HTTP
HTTP는 간단하게 말해서 인터넷을 작동시키게 만드는 프로토콜입니다.<br>
웹 서버 및 브라우저 간의 데이터를 전송하는 응용계층 프로토콜 입니다.

### HTTPS
HTTPS는 HTTP와 같은 방식으로 작동하는 프로토콜입니다.<br>
그러나 데이터를 전송할 때 암호화를 하여 전송합니다. 그러므로 데이터를 훔치거나, 해킹하지 못하도록 데이터를 전송합니다.




### HTTP 연결과정
HTTP연결과정을 TCP/IP 4계층의 관점에서 보면 4계층인 Application Layer에서 HTTP전송에 필요한 메세지를 작성하고, 3계층인 Transport Layer에서 클라이언트와 서버를 연결하고,
2계층인 Internet Layer에서 데이터를 패킷으로 나누는 과정을 거치고, 1계층에서 데이터를 전송하게 된다.

1. 브라우저가 URL을 입력하고 엔터를 친다.
2. HTTP요청은 DNS서버로 연결되서 IP주소를 찾는다. IP주소가 발견되지 않는다면 DNS서버를 추가해서 IP주소를 받아온다.
3. IP정보를 받게 되면 IP주소로 HTTP연결을 시도한다.
4. 신뢰성 보장을 위해 3번의 패킷 교환과정을 거침(3 way handshake)
5. 서버로 요청을 시도한다.
6. 서버에서 응답을 보낸다.
7. 서버와 클라이언트의 연결을 끊기 위해 4번의 패킷교환과정을 거친다.(4 way handshake)
8. 브라우저에 결과를 보여준다.