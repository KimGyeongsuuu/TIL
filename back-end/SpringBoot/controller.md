# controller
스프링 프레임워크의 `controller`은 사용자가 화면에서 어떠한 이벤트를 했을 경우, 그 이벤트에 해당하는 화면이나 기능을 실행할 수 있도록 해준다.

### 역할
+ Data receive
+ Interpret
+ Validate input data
+ Update View
+ Modify Model

### 생성
스프링 프레임워크에서 controller를 생성하려면 `@controller`어노테이션을 추가해 주면 된다. 어노테이션을 추가하게 되면 자동으로 bean이 등록되어 controller를 사용할 수 있다.

#### controller를 사용하려면 아래의 코드를 import해주어야 한다.
```java
import org.springframework.stereotype.Controller;
```
#### 클래스를 생성하고 그 위에 `@Controller `어노테이션을 추가한다.
```java
@Controller
public class BoardController {

}
```

### 라우팅 어노테이션
controller클래스에 라우팅을 할 수 있다. 요청 URL에 대해 해당하는 메소드를 매핑하기 위해 `@ReqestMapping` 어노테이션을 사용하자

#### @RequestMapping 어노테이션을 사용하려면, 아래의 코드를 import하면 된다.
```java
import org.springframework.web.bind.annotation.RequestMapping;
```
아래의 코드처럼 controller클래스 아래에 하나의 메소드를 만들고 `@RequestMapping`어노테이션을 추가하고, 호출 URL을 넣어준다.
```java
@Controller
public class Test_Controller extends BaseController {
	
	@RequestMapping("/a/b/json/test.*")
	public String test(HttpServletRequest request, Map model) throws SQLException{
		
		return JSON_VIEW;
	}
}
```

### 리턴
아래의 코드를 보면 return 다음에 " "가 있는데 " "안에 있는 파일로 이동하여 그 파일을 화면에 구현한다.
```java
@GetMapping("/board/write") //localhost:8090/board/write
public String boardWriteForm() {

    return "boardwrite";
}
```

# GetMapping
@GetMapping("hello")라고 적으면
이는 localhost:8080/hello 요청이 들어오면 아래의 함수를 실행하라고 해석하시면 됩니다.
```java
@Controller
public class HelloController {

    @GetMapping("hello")
    public String hello(){
        return "hello";
    }
}
```