 # MVC구조
Spring MVC는 Spring에서 제공하는 웹 모듈로, **Model**, **View**, **Controller** 세가지 구성요소를 사용해 사용자의 다양한 HTTP Request을 처리하고 단순한 텍스트 형식의 응답부터 REST 형식의 응답은 물론 View를 표시하는 html을 return하는 응답까지 다양한 응답을 할 수 있도록 프레임웍이다.

### 장점
+ 비즈니스 처리 로직과 사용자 인터페이스를 구분시켜 서로 영향 없이 개발이 가능하다는 장점이 있다.
+ Spring MVC는 웹 어플리케이션을 유연하고 확장 가능하게 만들어준다.
+ 사용자가 `Controller`에서 조작을 하면 `Model`을 통해 정보를 가지고 오고 `View`를 통해 시각화 한다.

![mvc](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbDpdks%2FbtrjV9EuRJ3%2FegwkkBELr5i0oYOv4t9Qy1%2Fimg.png)
### Model
+ 모델은 애플리케이션이 무엇을 할지에 대해 정의한다.
처리되는 데이터, 데이터베이스, 내부 알고리즘 등 내부 비즈니스에 관한 로직의 처리를 수행한다. 즉, 사용자에게 보이지 않는 로직.
### View
+ 뷰는 말 그대로 사용자에게 보여지는 영역이다. JSP등 사용자 인터페이스를 담당한다.
### Controller
+ 컨트롤러는 모델에게 어떻게 할 것인지를 알려주며, 모델과 뷰 사이를 연결하는 역할을 한다. 사용자의 입출력을 받아서 데이터를 처리한다.


### 웹에 적용
+ 사용자가 웹을 사용
+ `Controller`은 웹을 서비스하기 위해 `Model`를 호출
+ `Model`은 데이터베이스에서 값을 return
+ `Model`에서 리턴받은 값을 `View`에서 시각화
+ 사용자에게 웹이 보여진다.

### 방식
+ 모델1 방식 : JSP에서 출력과 로직을 전부 처리
+ 모델2 방식 : JSP에서 출력만 처리


![model1](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2Fw08Lw%2FbtrlbKqhWKO%2FqUYnM7xziHIQUE28L6WBZ1%2Fimg.png)
+ Model 1의 장점 : 빠르고 쉽게 개발이 가능하다
+ Model 1의 단점 : 유지보수가 어렵다.

#### Model 2
모델 2 방식은 사용자의 요청을 `Controller`가 받아서 `View`로 구현할지 `Model`로 보낼 것인지 판단하여서 보냅니다.

![model2](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FbGZKd4%2FbtrleqFoykC%2FkXkFFucLJdHJ4hNvfcmav0%2Fimg.png)
+ Model 2의 장점 : 디자이너와 개발자의 분업이 가능하고, 유지보수, 확장에 유이하다.
+ Model 2의 단점 : 개발하기가 어렵다

### 요약
+ Model : 백그라운드에서 동작하는 로직을 처리
+ View : 정보를 화면에 나타나게 하는 역할
+ Controller : 화면과 Model과 View를 연결해주는 역할