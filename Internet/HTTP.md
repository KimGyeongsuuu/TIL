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
