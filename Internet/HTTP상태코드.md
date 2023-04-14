# HTTP상태코드
HTTP요청을 했을 때 요청의 처리 상태를 알려주는 코드

+ 1xx (Informational): 요청이 수신되어 처리중
+ 2xx (Successful): 요청 정상 처리
+ 3xx (Redirection): 요청을 완료하려면 추가 행동이 필요
+ 4xx (Client Error): 클라이언트 오류, 잘못된 문법등으로 서버가 요청을 수행할 수 없음
+ 5xx (Server Error): 서버 오류, 서버가 정상 요청을 처리하지 못함

**만약에 모르는 상태코드가 나온다면**
+ 클라이언트는 상위 상태코드를 해석하여서 처리
```
299 -> 2XX(Successful)로 처리
455 -> 4XX(Client Error)로 처리
512 -> 5XX(Serve Error)로 처리
```

### 2XX(Successful) - 성공
클라이언트 요청이 성공적으로 처리되었을때

+ 200 OK
    + 요청 성공
+  201 Created
    + 요청에 성공하고, 새로운 리소스가 생성
+  202 Accepted
    + 요청은 성공하였지만, 처리는 완료되지 않았다.
+  204 No Content
    + 요청에는 성공하였지만, 본문에 보낼 데이터가 없다.

### 3XX() - 리다이렉션
요청을 완료하기 위해 유저 에이전트의 추가 조치 필요
+ 300 Multiple Choices
+ 301 Moved Permanently
+ 302 Found
+ 303 See Other
+ 304 Not Modified
+ 307 Temporary Redirect
+ 308 Permanent Redirect

리다이렉션은 응답 메시지에 Location헤더가 있으면 자동으로 Location위치로 이동한다.

### 리다이렉션의 종류
+ 영구 리다이렉션 - 특성 리소스의 URL이 영구적으로 이동
    + 301,308
    + ex) /members -> /users
    + ex) /event -> /new-event

+ 일시 리다이렉션 - 일시적인 변경
    + 302, 307, 303
    + 주문이 완료되면 주문 내역 화면으로 이동

### PRG(Post Redirect Get)
일시적인 리다이렉션

+ POST로 주문한 후에 새로고침을 하면 중복주문이 이루어질 수 있다.

해결

+ POST로 주문한 후에 GET으로 리다이렉트
+ 새로고침을 하면 GET으로 조회
+ 새로 고침 해도 GET으로 결과 화면만 조회



### 4XX(Client Error) - 클라이언트 오류
클라이언트가 요청할 때 생기는 오류<br>
클라이언트가 잘못된 데이터를 요청하기 때문에 계속 새로고침해도 같은 오류가 발생함

+ 400 Bad Request
    + 이 응답은 문법이 잘못되었을때 발생하는 에러입니다. 서버가 요청을 이해할 수  없을때 발생합니다.

### 5XX(Server Error) - 서버 오류
서버 문제로 오류가 발생<br>
서버의 오류이기 때문에 다시 새로고침을 하면 성공할 수도 있다.