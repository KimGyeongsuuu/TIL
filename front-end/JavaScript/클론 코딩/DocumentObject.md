# HTML in Javascript
`getElementById`는 id를 통해서 element를 찾아준다
"title"이란 아이디의 element를 찾아줄것이다
```js
document.getElementById("title");
```
`getElementByTagName`는 anchor,div,section,button같은 것을 의미합니다
```js
const title - document.getElementsByTagName("h1");
```
`innerText`는 titile명을 바꾸고 싶으면 아래와 같이 입력하면 된다.
```js
title.innerText("바꿀내용");
```
querySelector란?
+ html의 클래스 이름 및 태그를 갖고 오기 위해서 사용한다
+ 첫번째 element만 가져온다
+ 모두 가져오고 싶다면 `querySelectorAll`으로 적는다

index.html
```html
<body>
    <div class = hello>
        <h1>Hello Selector</h1>
    <div>
    <script = src="main.js></script>
</body>
```
main.js
```js
const title = document.querySelector(".hello h1"); 
console.log(title); // 결과 <h1> Hello Selector <h1>
```