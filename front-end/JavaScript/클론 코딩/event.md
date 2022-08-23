# Event
Event란?
+ 어떠한 사건을 의미한다.
  
  ex) 무언가를 클릭했을때 , 커서를 타이틀 위에 올릴 때

+ Event Binding

서로 묶어서 연결해 주는 것을 의미한다.
발생할 이벤트와 연결할 함수를 묶어서 연결해 주는 것이다.
예를 들어 클릭을 하게 되면 `click`이벤트가 발생하고, 이벤트가 발생했을때 일어나는 일을 콜백함수로 실행하게 된다.
콜백함수를 이벤트 핸들러라고 한다.

+ 바인딩 3가지 방식

```
1. HTML 이벤트 핸드러
2. 전통적인 DOM 이벤트 핸들러
3. Event Listener를 이용한 이벤트 핸들러
(3번의 방법이 1,2번의 단점을 보완한 방식이다)
```
1. HTML 이벤트 핸들러
HTML 요소의 이벤트 Attribute에 이벤트 핸들러를 대응시키는 방법이다.
```js
<button onclick = "click()">Click me</button>

function click(){
    alert('Button clicked!');
}
```
2. 전통적인 DOM 이벤트 핸들러 :
    + HTML과 Javasript가 혼용되는 문제가 해결되었다.
    + 단접
        + 이벤트 핸들러에 하나의 함수만을 바인딩할 수 있다.
        + 함수에 인수를 전달할 수 없다.
        + 바인딩한 핸들러가 2개이면 제일 마지막에 있는 핸들러만 실행한다.
```js
<button id = "myBtn">Click me</button>
var myBtn = document.getElementById('myBtn');
// 첫번째 바인딩된 이벤트 핸들러 => 실행되지 않는다.
myBtn.onclick = function(){
    alert('Button clicked 1');
};
// 두번째 바인딩된 이벤트 핸들러 =>실행이 된다.
myBtn.onclick = function(){
    alert('Button clicked2');
}

```
3. Event Listener를 이용한 이벤트 핸들러

addEventListener함수를 이용하여 이벤트를 바인딩하고, 해당 이벤트가 발생되었을 때 실행될 콜백함수를 지정한다.
```js
function handleTitleClick(){
    console.log("title was clicked!"); // 마우스가 타이틀을 클릭했을때
}
function handmouseenter(){
    console.log("mouse is here");  // 커서가 타이틀 위에 있을때
}
function handmouseleave(){
    console.log("mouse is leave"); // 커서가 타이틀 밖에 있을때
}
title.addEventListener("click",handleTitleClick); 
// 클릭을 하면 handleTitleClick이라는 함수가 실행이 된다.
title.addEventListener("mouseenter",handmouseenter);
// 타이틀위에 커서가 있으면 handmouseenter이라는 함수가 실행이 된다.
title.addEventListerner("mouseleave",handmouseleave);
// 타이틀밖에 커서가 있으면 handmouseleave이라는 함수가 실행이 된다.
```


