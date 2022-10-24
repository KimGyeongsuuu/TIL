# CRUD
CRUD는 데이터 처리 기능인 `CREATE`,`READ`,`UPDATE`,`DELETE`를 말한다.<br>
+ Create로 표의 데이터를 생성하고
+ Read로 표의 데이터를 읽고
+ Update로 표의 데이터를 갱신하고
+ Delete로 표의 데이터를 삭제한다

|이름|조작|SQL|
|--|--|--|
|CREATE|생성|INSERT|
|READ|읽기|SELECT|
|UPDATE|갱신|UPDATE|
|DELETE|삭제|DELETE|


### CREATE
`CREATE`는 DB에서 Table를 생성할 때 사용하는 명령어이다. CREATE TABLE table명();의 형태로 생성하는 것이 일반적이고 table명은 소문자로 지정한다.

#### 생성예시
```sql
CREATE TABLE member (
id INTEGER,
name VARCHAR(10),
phone_number VARCHAR(13)
);
```
<hr>

### INSERT
INSERT는 CREATE로 생성한 Table에 값을 삽입하는 것이다.<br>
문자열 타입인 데이터를 ''안에 넣어야하고, 숫자형 타입은 ''없이 숫자만 입력한다.
#### 삽입예시
```sql
INSERT INTO members VALUES (1, '왕밤방', '010-1234-4321');
```
<hr>

### SELECT
SELECT는 조회로 Table안의 값을 조회할 때 사용하는 명령어이다.
```sql
SELECT * FROM member
```
위에 코드는 member라는 Table의 전체 데이터를 모두 조회하겠다는 의미이다.

<hr>

### UPDATE
테이블의 내용을 수정하려고 할때 UPDATE명령어를 사용한다.
```sql
UPDATE member SET name = '왕밤빵';
```
위에 SELECT문을 사용하면 기존의 `왕밤빵`값을 `왕밤빵`으로 변경할 수 있다.

<hr>

### Where(조건)
만약에 테이블에서 '황미미'라는 사람의 전화번호만 바꾸고 싶다면 `WHERE colume = data`의 형식으로 조건을 두고 사용하면 된다.
```sql
UPDATE member SET phone_number='010-8888-9999' WHERE name='황미미';
```

<hr>

### DELETE
Table의 값을 삭제시키고 싶을때 DELETE명령어를 사용하면 된다.
```sql
DELETE FROM member WHERE name='김방봉'
``` 
김밥봉이라는 사람의 이름을 삭제시키고 싶으면 위의 코드처럼 삭제시키면 된다.

<hr>

### DROP
DROP은 Table의 특정한 값을 지우는 것이 아니라 Table전체를 지우고 싶을때 사용하는 명령어이다.
```sql
DROP TABLE member
```
위의 코드는 member라는 Table를 삭제시키는 코드이다.