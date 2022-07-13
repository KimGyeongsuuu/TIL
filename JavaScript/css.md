# css
### add
+ add는 classList에 class를 추가하는 기능이다
```js
function add(){
    h1.classList.add(clicked);
}
```
### remove
+ remove는 classList에 class를 삭제하는 기능이다
```js
function remove(){
    h1.classList.remove(clicked);
}
```
### toggle
+ toggle은 classList에 class name이 포함되었다면 제거하고, 포함되지 않았다면 추가하는 기능이다.
```js
const h1 = document.querySelector("div.hello:first-child h1");
function handelTitleClick(){
    h1.classList.toggle("clicked");
}

h1.addEvent Listener("click",handleTitleClick);
```