# CANVAS
### 사각형 그리기
+ rect(x좌표,y좌표,너비,높이);
+ X좌표가 200, Y좌표가 280이고 너비가 40 높이가 220인 사각형을 그립니다.
+ `rect`는 선을 그리기만 하고 출력은 하지 않은 상태 `fill()`함수를 사용해야지 도형이 출력이 됩니다.
```js
const canvas = document.querySelector("canvas");
const ctx = canvas.getContext("2d");
ctx.rect(200,280,40,220);
ctx.fill();
```
### 선 그리기
+ moveTo(x좌표,y좌표);
+ `moveTo`는 선을 그리는 시작점이고,`lineTo`위치로 선을 그립니다.
+ 선을 출력할 때는 `stroke()`함수를 사용합니다
```js
ctx.moveTo(150,300);
ctx.lineTo(400,100);
ctx.lineTo(650,300);
ctx.stroke();
```
### 원 그리기
+ arc(x좌표,y좌표,반지름,startAngle,endAngle);
    + startAngle : angle시작점
    + endAngle   : angle 끝나는점

    + angle값에 따른 위치
    ![angle값에 따른 위치](https://webisfree.com/static/uploads/2018/2066_arc_angle.jpg)
```js
ctx.arc(430,630,8,0,2*Math.PI);
```
### beginPath
+ `beginPath`는 도형을 그릴 경로를 초기화 시키는 겁니다.
### 도형의 스타일
+ 색 변화 
    ```
    ctx.fillStyle ="red";
    ```
