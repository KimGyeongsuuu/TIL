# @PathVariable
REST API에서 URI에 변수가 들어가는걸 실무에서 많이 볼 수 있다.
예를 들면, 아래 URI에서 밑줄 친 부분이 @PathVariable로 처리해줄 수 있는 부분이다.

http://localhost:8080/api/user/<u>1234</u>

https://music.bugs.co.kr/album/<u>4062464</u>

### 사용법
+ Controller에서 GetMapping에 {변수명}
+ 메소드 정의할 때 변수명에 @PathVariable("변수명")을 붙여준다.
```java
@RestController
public class MemberController { 
    // 기본
    @GetMapping("/member/{name}")
    public String findByName(@PathVariable("name") String name ) {
        return "Name: " + name;
    }

    // 여러 개
    @GetMapping("/member/{id}/{name}")
	public String findByNameAndId(@PathVariable("id") String id, @PathVariable("name") String name) {
    	return "ID: " + id + ", name: " + name;
    }
    
}
```

### 주의할 점
+ Spring 에서 @PathVariable 사용하여 값을 넘겨받을때 값에 . 가 포함되어 있으면 .포함하여 그뒤가 잘려서 들어온다는 것!


### RequestParam과의 차이점
`RequestParam`과 `PathVariable` 둘 다 데이터를 받아오는데 사용된다.<br>
그러나 RequestParam은 많은 데이터를 받아올 수 있지만, PathVariable은 하나의 데이터만 받아올 수 있다.<br>
RequestParam은 uri로 전달받은 값이 아니더라도, ajax 요청을 통해 body에 담은 데이터를 여러 타입으로 받을 수 있다.


+ PathVariable : http://localhost:8080/api/user/<u>1234<u>
+ RequestParma : http://localhost:8080/api/user?id=kim%name=gyeongsu


