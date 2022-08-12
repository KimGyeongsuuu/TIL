# CSS 스타일
### 박스 스타일
![box](https://4.bp.blogspot.com/--9k4VxagyFk/UUkkJcIuIfI/AAAAAAAAAKw/ot2DEkkPEUU/s1600/1.png);
+ content : 실제 내용
+ padding : content와 테두리 사이의 공간
+ border : 테두리 두께
+ margin : 테두리와 최종경계 사이의 두께

`margin`이나 `padding`을 사용할 때 1번 처럼 하나씩 하기 보다는 2번 처럼 한 번에
위,오른쪽,아래,왼쪽 순으로 사용하는것이 더 편리하다.
```css
// 1번
div#box3{
    margin-top: 400px;
    margin-right: 100px;
    margin-bottom: 400px;
    margin-left: 100px;

    padding-top: 200px;
    padding-right: 400px;
    padding-bottom: 200px;
    padding-left: 400px;
}
```
```css
// 2번
div#box3 {
    margin: 400px 100px 400px 100px;

    padding: 200px 400px 200px 400px;
}
```
### 테두리 스타일
+ border-width : border의 **굵기**를 지정
+ border-color : border의 **색깔**을 지정
+ border-style : border의 **스타일**을 지정 
    + border-style의 종류
        + solid : 기본 선
        + dotted : 도트 선(점으로 된 선)
        + groove : 음영이 들어간 선(리듬감을 주는 느낌)
        + ridge : `groove`보다 살짝 진한 선
        + double : 두줄 선(3px이상일 때만 구분 가능)
        + inset : 안으로 들어간 음영(왼쪽과 위쪽을 진하게)
        + outset : 튀어나온 음영(오른쪽과 아래쪽을 진하게)
        + dashed : 점선
        + none : 아무것도 없는 상태
        + mixed : margin과 padding과 같이 위,오른,아래,왼쪽 순서대로 border가 디자인 된다.
        + border-radius : 둥글게 한다

        ![style](https://blog.kakaocdn.net/dn/ccbCgJ/btq7sYVrxtC/ysDctqacpZMsbQCVn4whJ0/img.jpg);

### 배경 스타일
##### background-color : 배경 색 지정하기
``` css
background-color : <색상>
```
##### background-img : 웹 요소에 이미지 넣기
```css
background-img : url(파일경로)
```
##### background-repeat : 배경 이미지 반복 방법 지정하기
+ 이미지가 채우려는 요소 크기보다 작을 경우, 해당 요소를 이미지가 반복되며 가득 채웁니다. 어떤 방법으로 가득 채울지 `background-repeat`속성으로 지정할 수 있습니다. 

|속성 값|설명|
|---|:---:|
|repeat|브라우저 화면에 가득 찰 때까지 배경 이미지를 가로와 세로로 반복합니다.|
|repeat-x|브라우저 창 너비와 같아질 때까지 배경 이미지를 가로로 반복합니다.|
|repeat-y|브라우저 창 높이와 같아질 때까지 배경 이미지를 세로로 반복합니다.|
|no-repeat|배경 이미지를 한 번만 표시하고 반복하지 않습니다.|

### 텍스트 스타일
##### 글자 크기
+ `font-size`는 텍스트의 크기를 조절할 때 사용합니다.
+ medium : 웹브라우저에서 정한 기본 글자크기입니다.
+ xx-small, x-small, small, large, x-large, xx-large : medium에 대한 상대적인 크기입니다.
+ smaller, larger : 부모 요소의 글자 크기에 대한 상대적인 글자 크기입니다.
+ length : px, %, em, rem 등으로 크기를 정합니다.
+ initial : 기본값으로 설정합니다.
+ inherit : 부모 요소의 속성값을 상속받습니다
##### 글자 위치
+ `text-align`은 글자를 왼쪽 정렬, 오른쪽 정렬, 가운데 또는 양쪽 정렬할지를 설정할 때 사용합니다.
+ left : 기본값으로 글자를 왼쪽에 정렬한다.
+ center : 글자를 가운데에 정렬한다.
+ right : 글자를 오른쪽에 정렬한다.
+ justify : 글자를 양쪽에 정렬한다.
##### 폰트 스타일
+ `font-family`는 텍스트의 글꼴이나 서체를 변경할 때 사용합니다.
+ serif : 삐침 있는 명조 계열의 글꼴 
+ sans-serif : 삐침 없고 굵기가 일정한 고딕 계열의 글꼴
+ monospace : 글자 폭과 간격이 일정한 글꼴
+ cursive : 손으로 쓴 것 같은 필기 계열의 글꼴
+ fantasy : 화려한 글꼴
    