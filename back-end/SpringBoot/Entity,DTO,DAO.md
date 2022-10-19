# DAO
+ DAO는 실제로 DB에 접근하는 객체이다.
+ Service와 DB를 연결하는 역할을 한다.
+ SQL문을 사용하여서 DB에 접근한 후 적절한 CRUD API를 제공한다.

![DAO](https://user-images.githubusercontent.com/58545240/121490721-40c6f400-ca10-11eb-8425-1a1260e720e9.png)

# DTO
계층간 데이터 교환을 하기위한 객체
+ DB에서 데이터를 얻어서 Service나 Controller에 전달할 때 쓰이는 객체를 말한다.
+ 로직은 가지고 있지 않고, 매서드는 getter,setter 만을 가진다.
### Request와 Response용 DTO는 View를 위한 클래스
+ 자주 변경이 필요한 클래스
+ toEntity메서드를 사용하여서 DTO에서 필요한 부분을 이용하여 Entity를 만든다.

# Entity class
### domain package
**실제 DB의 테이블관 매칭도리 클래스**
+ 즉, 테이블의 링크도리 클래스
+ @Entity, @Column, @Id 등의 어노테이션을 사용한다.
+ 실제 DB테이블과 매칭될 클래스이다.
+ Entity는 Setter를 설정하지 않는다.
+ Entity와 DTO는 다른 것으로 View와 DB분리가 확실하게 이루어져야 한다.


### 패키지의 전체 구조
![Entity](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRBeEFMTQd7elP06MfiSFnOQBY4X9pZXkQq0Q&usqp=CAU)

#### Controller
+ 기능
    + url에 따라 적절한 view를 처리한다.
    + DTO를 Body에 담아서 Client에 전송한다.

+ @Controller
    + API와 view를 동시에 사용하는 경우
    + 주목적은 return해서 화면에 view를 구현하는 것
    ```java
    @Controller
    @RequestMapping("/")
    public class HomeController {
        @GetMapping
        public String home(HttpSession session) {
            if (!SessionUtil.getUser(session).isPresent()) {
                return "login";
            }
            return "index";
        }
    }
    ```

+ @RestController
    + view가 필요없는 api만 지원하는 서비스
    + 주목적은 data를 return하는 것 이다.
    + @RestController = @Controller + @ResponseBody
    ```java
    @RestController
    @RequestMapping("/api/users")
    public class ApiUserController {
        @Autowired
        private UserService userService;

        @PostMapping("/login")
        public ResponseEntity login(@RequestBody @Valid LoginDto loginDto, HttpSession session) {
            SessionUtil.setUser(session, userService.login(loginDto));
            return new ResponseEntity(HttpStatus.OK);
        }
    }
    ```
#### Service
+ 기능
    + @Autowired Repository를 통해 repository에 method를 이용한다.
    + 적절한 비즈니스 로직을 처리한다.
    + DAO로 DB에 접근하여서 DTO로 데이터를 전달 받고, 비즈니스 로직을 처리하여서 데이터를 반환한다.
    ```java
    @Service
    public class UserService {
        @Autowired
        private UserRepository userRepository;
        @Resource(name = "bCryptPasswordEncoder")
        private PasswordEncoder bCryptPasswordEncoder;
        @Autowired
        private MessageSourceAccessor msa;

        public User save(UserDto userDto) {
            if (isExistUser(userDto.getEmail())) {
                throw new UserDuplicatedException(msa.getMessage("email.duplicate.message"));
            }
            return userRepository.save(userDto.toEntityWithPasswordEncode(bCryptPasswordEncoder);
        }
    }
    ```
    #### Repository(DAO)
    + 실제로 DB에 접근하는 객체
    + Service와 DB를 연결한다.