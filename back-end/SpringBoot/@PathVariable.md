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
