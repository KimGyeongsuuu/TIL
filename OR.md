# 논리 연산자
+ || (OR)
    + OR는 첫번째 true를 발견하면 즉시 평가를 멈춘다.
    + A 나  B중 true가 있으면 ture
+ && (AND)
    + &&는 첫번째 false를 발견하면 즉시 평가를 멈춘다.
    + A 와 B 모두 true여야지 true
    + 둘 중 하나라도 false라면 false
+ ! (NOT)
```js
const age = prompt("나이가..?");
const isAudlt = age > 19;

if(!isAudlt){ 
    console.log("돌아가..");
}
```

