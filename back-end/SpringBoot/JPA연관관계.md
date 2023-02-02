# JPA 연관관계
### 연관관계 매핑
**객체와 관계형 데이터베이스 테이블 서로 매핑하는 것**

연관관계 매핑할 때 생각해야할 3가지가 존재한다.
+ 방향 : 단방향, 양방향 (객체 간의 참조)
+ 다중성 : 일대일, 일대다, 다대일, 다대다
+ 연관관계의 주인 : 양방향일 때 연관관계에서 관리의 주체가 되는 곳

### 다중성
+ 다대일(N : 1)[ManyToOne]
+ 일대다(1 : N)[OneToMany]
+ 일대일(1 : 1)[OneToOne]
+ 다대다(N : N)[ManyToMany]

### 방향
방향에는 단방향, 양방향이 있습니다

DB테이블에서는 외래키 하나로 조인(join)을 사용해서 양방향 쿼리가 가능합니다.
따라서 DB에는 양방향 개념이 없습니다.

그러나 객체의 경우 자신이 참조한 객체만 연관관계를 조회할 수 있기에 방향의 개념이 존재합니다.

객체관계에서 한 쪽만 반대쪽을 참조하는 경우 `단방향`이라고 하고, 서로 참조하는 경우 `양방향`이라고 합니다.


### 연관관계의 주인
DB에서는 외래키로 두개의 테이블이 연관관계를 맺습니다.

양방향으로 연관관계를 맺으면, A -> B, B -> A 두 곳에서 서로 참조함으로,
연관관계를 관리하는 포인트는 두 곳이 됩니다.

이 JPA연관관계에서 두 객체중 하나의 객체를 연과관계의 주인으로 설정해야 합니다.<br>
외래키를 관리하는 객체가 연관관계의 주인이 됩니다.

외래키를 관리하는 주인만 외래 키를 변경시킬 수 있으며, 주인이 아닌 객체는 읽는것만 가능합니다.

연관관계의 주인이 아닌 객체에서 `mappedBy`를 사용해서 주인을 지정해 줍니다.

`TIP : 외래 키가 있는 곳을 연관 관계의 주인으로 정하면 됩니다. 무조건!!!!`



### 다대일[N : 1] - @ManyToOne
`게시판(board)`과 `게시글(post)`의 관계를 예로 들겠습니다.

+ 요구사항
    + 하나의 게시판(1)에 여러글(N)을 작성할 수 있다.
    + 하나의 게시글은 하나의 게시판에만 작성 가능하다.


**단방향**
```java
@Entity
public class Post{
    @Id
    @GeneratedValue
    @Colume(name = "POST_ID")
    private Long id;

    @Colume(name = "TITLE")
    private String title;

    @ManyToOne
    @JoinColumn(name = "BOARD_ID")
    private Board board;
}

@Entity
public class Board{
    @Id
    @GeneratedValue
    private Long id;
    private String title;
}
```

다대일 단방향에서는 `다`쪽인 Post에서 `@ManyToOne`만 추가하면 됩니다.<br>
단방향이기에 Board에는 아무것도 참조하지 않습니다.

**양방향**
```java
@Entity
public class Post{
    @Id
    @GeneratedValue
    @Colume(name = "POST_ID")
    private Long id;

    @Colume(name = "TITLE")
    private String title;

    @ManyToOne
    @JoinColumn(name = "BOARD_ID")
    private Board board;
}

@Entity
public class Board{
    @Id
    @GeneratedValue
    private Long id;
    private String title;

    @OneToMany(mappedby = "board")
    List<Post> posts = new ArrayList();
}
```
다대일에서 양방향을 사용하려면 `다대일`에서 `일`쪽에 `@OneToMany`어노테이션을 추가해주고 `@maapedBy`로 연관관계의 주인을 정해줍니다.

### 일대다[1 : N] - @OneToMany
일대다는 다대일과 거의 비슷하지만 `다대일`에서의 연관관계의 주인은 `다`쪽이 었지만 `일대다`의 주인은 `일`쪽이라는 차이점이 있다.

**단방향**<br>
데이터베이스에서는 무조건 N(다)쪽에서 외래키를 관리합니다.<br>
그렇지만 `일`쪽에서 `다`를 생성,수정,삭제하는 방법이 있다.

```java
@Entity
public class Post {
    @Id @GeneratedValue
    @Column(name = "POST_ID")
    private Long id;

    @Column(name = "TITLE")
    private String title;
}

@Entity
public class Board {
    @Id @GeneratedValue
    private Long id;
    private String title;

    @OneToMany
    @JoinColumn(name = "POST_ID") //일대다 단방향을 @JoinColumn필수
    List<Post> posts = new ArrayList<>();
}
```
일대다의 단방향의 경우 `@OneToMany`에 `mappedBy`를 사용할 필요가 없습니다.
대신 `@JoinColumn`을 이용해서 조인을 합니다.


**양방향**<br>
`일대다` 양방향은 공식적으로 존재하는 것이 아니여서 생략하겠습니다.<br>
`일대다` 양방향을 사용해야할 때는 `다대일` 양방향 사용하도록 하는게 더 좋습니다.

### 일대일[1 : 1] - @OneToOne
주 테이블에 외래키를 넣을 수도 있고, 대상 테이블에 외래키를 넣을 수도 있습니다.<br>
**일대일**이기 때문에 A,B테이블이 있을때, A테이블이 주 테이블이면 B테이블이 대상테이블이고, B테이블이 주 테이블이면 B테이블이 대상테이블입니다.

**단방향**
```JAVA
@Entity
public class Post {
    @Id @GeneratedValue
    @Column(name = "POST_ID")
    private Long id;

    @Column(name = "TITLE")
    private String title;

    @OneToOne
    @JoinColumn(name = "ATTACH_ID")
    private Attach attach;
}
@Entity
public class Attach {
    @Id @GeneratedValue
    @Column(name = "ATTACH_ID")
    private Long id;
    private String name;
}
```
일대일 단방향도 거의 지원하지 않습니다.

**양방향**

양방향도 다를게 없다. 기존 단방향코드에 `@OneToOne`을 설정하고 `mappedBy`를 통해 읽기 전용으로 만들어주면 됩니다.
```java
@Entity
public class Attach {
    @Id @GeneratedValue
    @Column(name = "ATTACH_ID")
    private Long id;
    private String name;

    @OneToOne(mappedBy = "attach")  
    private Post post;
  //... getter, setter
}
```

### 다대다[N : N] - ManyToMany
+ 실무사용 금지
