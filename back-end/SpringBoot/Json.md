# JSON
### JSON이란
+ `JavaScriptObjectNotion`의 약자로 데이터를 교환할 때 사용하는 데이터교환 형식이다.
+ JSON표현식은 사람과 기계가 모두 이해하기 쉬우고 용량이 작아서, JSON XML을 대체하여 데이터 전송에 많이 쓰인다.
+ JSON은 문법이 아닌 데이터를 표시하는 표현방법이다.

### 특징
+ 서버와 클라이언트가 교류를 할 때 많이 쓰인다.
+ JavaScript를 이용하여 JSON문서를 JavaScript객체로 변환할 수 있다.
+ JavaScript의 형식을 기반으로 만들어졌다.
+ JavaScript의 객체 표기법과 유사하다.

### JSON문법
Json문법에는 `Key`값과 `Value`값이 존재하고 쌍따옴표를 이용하여 표기한다.<br>
자바스크립트의 객체처럼 원하는 만큼 중첩시켜서 사용할 수도 있다.
```java
{
  "employees": [
    {
      "name": "Surim",
      "lastName": "Son"
    },
    {
      "name": "Someone",
      "lastName": "Huh"
    },
    {
      "name": "Someone else",
      "lastName": "Kim"
    } 
  ]
}
```
### 형식
1. name/value형식의 JSON

    {String key : String value}
    ```java
    {
        "name": "Surim",
        "lastName": "Son"
    },
    ```

2. List형식의 JSON
    여러가지 언어들을 배열형식으로 구현한다.
    ```java
    {
        "firstName": "Kwon",
        "lastName": "YoungJae",
        "email": "kyoje11@gmail.com",
        "hobby": ["puzzles","swimming"]
    }
    ```