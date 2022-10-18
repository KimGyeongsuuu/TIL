# Thymeleaf
### 자주 사용하는 문법
<br>

### th:text 
화면에 값을 출력할 때 사용

```java
<span th:text="${nickname}"></span>
```

### th:if
조건문이다. 해당 조건이 맞으면 실행한다
```java
<div th:if="${error}">
        <p>에러 발생</p>
</div>
```

### th:errors
error가 발생하면 실행한다
```java
<ul>
    <li th:errors="*{id}" />
    <li th:errors="*{name}" /> 
</ul>
```

## form에서 사용하는 문법


### th:action
form태그를 사용할 때, 해당 경로로 요청을 보낸다.

### th:object
form에서 `submit`을 사용할 때, form의 데이터가 th:object에 설정해준 객체로 받아진다.

## 중복제거

### th:fragment
header, footer, navigation bar 와 같이 모든 페이지에서 보여져야하는 부분은 따로 분리하여 관리한다.

```java
// fragments.html
<head th:fragment="head">
    <meta charset="UTF-8">
    <title>StudyOlle </title>
    <link rel="stylesheet" href="/node_modules/bootstrap/dist/css/bootstrap.min.css"/>
    <style>
        .container {
            max-width: 100%;
        }
    </style>
</head>
```

## Utility
타임리프에서 `Utility`를 사용할때는 #을 사용한다.
```java
th:value="${#strings.listJoin(tags, ',')}"
```