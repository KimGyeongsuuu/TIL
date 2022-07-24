# todo  
### localstorage에 배열형식으로 저장하기
+ JSON.stringify()는 단순히 string으로 바꾼것이다.
+ JSON.parse()는 자바스크립트 object로 바꾼것이다.
```js
localStorage.setItem("todos", JSON.stringify(toDos));
```
### JS에서 html에 element를 생성하기
+ creatElement()를 사용하여서 document에 li를 생성합니다.
+ appendChild()는 creatElement에서 생성된 element를 문서에 있는 바디 요소의 끝에 붙입니다.
```js
const li = document.createElement("li")
const span = document.createElement("span");
const button = document.createElement("button");
span.innerText = value;
button.innerText = "❌";
button.addEventListener("click",deleteToDo);
li.appendChild(span);  // 생성된 element를 바디에 붙인다.
li.appendChild(button);  // 생성된 element를 바디에 붙인다.
toDoList.appendChild(li);
```
### for each
+ for each는 배열의 각 item에 대해 function을 실행하게 해주는 기능입니다.
```js
const savedToDos = localStorage.getItem(TODOS_KEY);
console.log(savedToDos);
if(savedToDos !== null){
    const parsedToDos = JSON.parse(savedToDos);
    parsedToDos.forEach(sayhello) // parsedToDos배열에 각 item마다 sayhello라는 함수를 실행시킨다.
}
```
### filter
+ 자바스크립트에서 filter 는 배열에 사용하며, 주어진 함수를 만족하는 모든 요소를 모아 새 배열로 반환한다.
+ 배열.filter(함수) 함수의 반환값이 true이면 요소를 유지하고, false이면 새 배열에 유지되지 않는다.
+ 사용법 1
```js
list.filter(function(word){
  return word.length >= 6 ;
})
```
+ 사용법 2
```js
let list = ["hello","world","javascript"];

function filterCallbackFunction(word){
    return word.length <= 6;
}

list.filter(filterCallbackFunction);
```
##### 결과
+ javascript는 6글자 이상임으로 위에 조건에 거짓임으로 새 배열에 유지되지 못하였다.
```
["hello","world"] 
```