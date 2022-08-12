# CSS속성
+ css에서는 특정한 기능을 하는 것들을 미리 정의되어있다.<br>
이를 속성이라고 한다.<br>
+ `속성 : 값`의 형태로 사용되며, 여러 속성끼리는 ;를 통해 구분됩니다.
```css
선택자{
    속성 : 값;
    속성 : 값;
}
```
### visibility 속성
+ `visibility`속성은 태그의 가시성을 결정합니다.
+ 4개의 값을 가지고 있으며, 기본값은 `inherit`입니다.
    + visible : 보임
    + hidden : 숨김
    + collapse : 겹치도록 지정
    + inherit : 부모 요소의 값을 상속

#### 사용법
```css
.class1{
    visibility: hidden;
}
```
### display 속성
+ `display`속성은 요소를 어떻게 보여줄지 결정합니다.
+ block : 일반적으로 `div`태그의 기본값 입니다.
+ inline : 줄바꿈이 되지 않는다.
+ none : 보이지 않음

#### none
+ 요소를 렌더링하지 않도록 설정합니다. hidden과 차이점은 hidden영역은 차지하지만 none은 영역도 차지 하지 않는다.

### position 속성
+ `position`속성은 HTML문서 상에서 요소가 배치되는 방식을 결정합니다.
position속성은 요소를 정확하게 지정하기 위해서 `top`,`right`,`bottom`,`left`속성과 함께 사용됩니다.
#### position: static
+ `position: static`을 사용하면 원래 html문서상에 위치 그대로 배치됩니다.
그래서 `top`,`right`,`bottom`,`left`들과 같은 속성값은 position 속성이 static일때는 모두 무시됩니다.
#### position: relative
+ `position: relative`을 사용하면 html문서상의 요소를 원래 위치에서 벗어나게 배치할 수 있습니다.`top`,`right`,`bottom`,`left`을 사용하여서 위치를 지정합니다.
```css
div:nth-of-type(2) {
  position: relative;
  top: 28px;
  left: 48px;
  background: cyan;
  opacity: 0.8;
}
```
#### position: absolute
+ `position: absolute`는 
#### position: fixed
+ `position: fixed`로 지정하면 항상 같은 위치에 지정되있습니다.화면을 스크롤하여도 그 위치 그대로 위치합니다.
+ 아래 코드를 보면 아래의 div태그는 `bottom`으로 부터 8px 떨어지고, `right`에서 16px떨어진 위치에 고정적으로 위치하게 됩니다.
```css
div:nth-of-type(2) {
  position: fixed;
  bottom: 8px;
  right: 16px;
  background: cyan;
  opacity: 0.8;
}
```
#### position: sticky
+ `position: sticky`는 브라우저를 스크롤링할 때 많이 사용합니다.
position이 sticky로 되어있을때 스크롤을 하면 해당요소는 화면상단에 고정되어서 
화면에서 사라지지 않습니다.
```css
div:nth-of-type(2){
    position: sticky;
    top: 0;
    background-color : cyan;
    opacity: 0.8;
}
```
### overflow 속성
+ `overflow`는 요소내의 콘텐츠가 넘쳐나서 요소에 모두 보여주기 힘든 상황일 때 모두 보여주기 위한 속성입니다.
```
+ scroll : 스크롤바가 추가되어 스크롤할 수 있습니다.
+ hidden : 넘치는 부분은 짤라낸다.
+ overflow-x : 스크롤 가로를 담당
+ overflow-y : 스크롤 세로를 담당
+ auto : 콘텐츠 양에 따라서 알아서 결정
```
### float 속성
+ `float`이란 뜻인 '뜨다'라는 의미 그대로 요소에 어떻게 띄울지 지정하는 속성입니다.
```
right : 오른쪽에 박스하나를 생성, 페이지 내용을 왼쪽 상단부터 시작
left : 왼쪽에 박스하나늘 생성, 페이지 내용을 오른쪽 상단부터 시작
none : 요소를 부여하지 않음
```