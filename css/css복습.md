# css
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
    color: gray;
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
+ 