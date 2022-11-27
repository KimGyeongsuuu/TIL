# HTTP메서드
### 주요 메서드
+ GET : 리소스 조회
+ POST : 요청 데이터를 처리
+ PUT : 리소스를 대체
+ PATCH : 리소스의 부분을 대체
+ DELETE : 리소스를 삭제

### GET

```
GET /search?q=hello&hl=ko HTTP/1.1  // 쿼리파라미터를 이용하여 전달
Host: www.google.com
```
GET은 이런식으로 보낸다. URL 뒤에 "?" 마크를 통해 URL의 끝을 알리면서, 데이터 표현의 시작점을 알린다.
데이터는 key와 value가 한 쌍으로 이루어진다.

+ 리소스 조회
+ 서버에 전달하고 싶은 내용을 쿼리 파라미터를 통하여서 전달
+ 전달한 내용을 메시지 바디를 이용하여서 전달할 수 있지만, 지원하는 곳이 많이 않아서 권장하지는 않는다.

### POST
```
POST /members HTTP/1.1 // 시작줄
Content-Type: application/json // 헤더
{   // 본문
 "username": "hello",   
 "age": 20
}
```
+ 요청 데이터를 처리
+ **메시지 바디**를 통하여서 서버로 데이터를 전달


### POST의 메시지 전달
```
POST /members HTTP/1.1
Content-Type: application/json
{
 "username": "young",
 "age": 20
}
```
1. 신규 리소스를 서버로 전달한다.

![img](/Internet/POST01.png)


2. 서버에서 신규 리소스를 생성해준다.

/members/1000
![img](/Internet/POST02.png)


3. 서버에서 클라이언트로 응답을 한다.


응답 데이터
```
HTTP/1.1 201 Created
Content-Type: application/json
Content-Length: 34
Location: /members/100
{
 "username": "young",
 "age": 20
}
```

![img](/Internet/POST03.png)


### POST가 사용되는 예시
+ HTML 양식에서 회원가입이나 주문을 할 때 사용된다.

+ 서버가 아직 식별하지 않은 새 리소스를 생성할 때 사용된다.

+ 기존 자원에 데이터를 추가할 때 사용된다.


### PUT
+ 리소스를 대체
    + 리소스를 요청했을 때 이미 리소스가 존재하면 그 리소스를 전부 대체한다.
    + 리소스가 존재하지 않으면 리소스를 생성한다.


1. 리소스가 있는 경우

요청한 데이터
```
PUT /members/100 HTTP/1.1
Content-Type: application/json
{
 "username": "old",
 "age": 50
}
```
서버 데이터
```
{
 "username": "young",
 "age": 20
}
```

결과 : 데이터가 `username`은 old가 되고 `age`는 50으로 대체된다.

2. 리소스가 없는 경우

요청한 데이터
```
PUT /members/100 HTTP/1.1
Content-Type: application/json
{
 "username": "young",
 "age": 35
}
```
서버 데이터
```

```

결과 : 데이터가 `username`은 young이되고 `age`는 35로 대체된다.

**주의할 점**

요청할 데이터
```
PUT /members/100 HTTP/1.1
Content-Type: application/json
{
 "age": 50
}
```
서버 데이터
```
{
 "username": "young",
 "age": 20
}
```

PUT요청은 리소스를 완전히 대체하기 때문에 `username`필드가 삭제가 되고 `age`는 50이 된다


### PATCH
PATCH는 부분적으로 대체가 가능하다.

요청 데이터
```
PATCH /members/100 HTTP/1.1
Content-Type: application/json
{
 "age": 50
}
```
서버 데이터
```
{
 "username": "young",
 "age": 20
}
```

`username`의 필드는 변화가 없고 `age`만 50으로 대체된다.


### DELETE
DELETE는 리소스가 제거된다.

요청 데이터
```
DELETE /members/100 HTTP/1.1
Host: localhost:8080
```

서버 데이터
```
{
 "username": "young",
 "age": 20
}
```

그냥 서버데이터가 삭제된다.

