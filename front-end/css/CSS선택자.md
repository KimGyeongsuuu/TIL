# CSS선택자
### 구성요소
+ 선택자(selector) : 스타일을 적용할 대상 지정
+ 속성명(property) : 속성의 이름
+ 속성값(value) : 속성에 적용할 값
+ 선택자 {속성명 : 속성 값;}과 같이 사용하여 스타일 적용
```css
p{
    color: blue;
    text-align: center;
}
```
### 적용 방법
+ 인라인 스타일 : HTML요소의 여는 태그에 style 속성으로 지정
+ 내부 스타일: 같은 HTML문서에서 style이라는 태그를 지정하고 사용
+ 외부 스타일: HTML과 다른 파일로 style지정

##### 인라인 스타일
```css
<p style="color: red; background-color:black">인라인 스타일<p>
```
##### 내부 스타일 
```css
<html>
    <head>
        <title>내부 스타일<title>
        <style>
        p{
            color:red;
            background-color: yellow;
        }
        </style>
    </head>
<html>
```
##### 외부 스타일
+ style.css라는 다른 문서에서 style을 지정

style.css
```css
p{
    color: green;
}
```
### 선택자
+ HTML에 모든 태그를 선택하는 전체 선택자
```css
*{
    color: gray; // color는 속성명, gray는 속성값
}
```
+ 특정 id 태그를 선택하는 id선택자
+ id를 태그 할 때는 `#`을 붙여줘야 한다.
```css
#name{
    color: black;
}
```
+ 특정 class 태그를 선택하는 class선택자
+ class를 태그 할 때는 `.`을 앞에 붙여줘야 한다.
```css
.grade{
    color: gold;
}
```
### 반응 선택자
+ `:link` : 방문하지 않은 링크
+ `:visited` : 방문한 링크
+ `:active` : 클릭하는 순간
+ `:hover` : 마우스 커서를 올려놓는 순간

### 구조 선택자
+ `E:nth-child(n)`n번째 순서인 E태그를 선택

css
```css
p:nth-child(1){background-color: blue;}
p:nth-child(2){background-color: blue;}
p:nth-child(3){background-color: blue;}
p:nth-child(4){background-color: blue;}
p:nth-child(5){background-color: blue;}
```
html
```html
<body>
    <p>Hello</p>
    <p>Hello</p>
    <p>Hello</p>
    <p>Hello</p>
    <p>Hello</p>
</body>
```
+ `E:first-child`는 같은 E태그에 첫번째 순서인 E태그를 선택
+ `E:last-child`는 같은 E태그에 마지막 순서인 E태그를 선택

css
```css
p:first-child{color: red;}
p:last-child{color: green;}
```
html
```html
<body>
    <p>hello</p>
    <p>hello</p>
    <p>hello</p>
<body>
```
### 상태 선택자
+ `input:enabled` : 입력이 가능한 input태그를 선택
+ `input:disabled` : 입력할 수 없는 input태그를 선택
+ `input:focus` : focus가 된 input태그를 선택

### 선택자 조합 방법
|종류|설명|
|-----|---|
|A B|선택자 B가 포함된 선택자 A 선택|
|A>B|선택자 A의 바로 직계 자손인 B 선택|
|A+B|A 선택자 바로 다음의 B선택자 선택|
|A~B|A 선택자 다음으로 가장 인접해있는 모든 선택자 B를 선택|
|A,B|A 선택자와 B선택자를 모두 선택|
