# Lombok
Lombok이란 Java에서 반복되는 메소드를 `Annotation을 사용하여 자동으로 작성해주는 라이브러리이다. 보통 DTO,Model,Entity의 경우 여러 속성이 존재하고 이들을 가지는 프로퍼터에 대해서 매번 getter(),setter(),생성자를 작성해야하는데 Lombok을 사용하면 자동으로 생성이된다.

### 사용하는 이유
+ Lombok을 사용하면 개발자가 해야할 귀찮은 코드 작성을 대신해준다는 좋은 점이 있다.
+ 반복적인 코드를 쓰지 않기 때문에 가독성과 유지보수에 유의하다.

### Lombok과 자바의 차이

BoardCategory라는 모델 클래스가 있다.
```java
public class BoardCategory {

    private String category_id;

    private String category_name;

    private Date regdate;

    private int board_cnt;

    private int seq;

    public String getCategory_id() {
        return category_id;
    }

    public void setCategory_id(String category_id) {
        this.category_id = category_id;
    }

    public String getCategory_name() {
        return category_name;
    }

    public void setCategory_name(String category_name) {
        this.category_name = category_name;
    }

    public Date getRegdate() {
        return regdate;
    }

    public void setRegdate(Date regdate) {
        this.regdate = regdate;
    }

    public int getBoard_cnt() {
        return board_cnt;
    }

    public void setBoard_cnt(int board_cnt) {
        this.board_cnt = board_cnt;
    }

    public int getSeq() {
        return seq;
    }

    public void setSeq(int seq) {
        this.seq = seq;
    }

    @Override
    public String toString() {
        final StringBuffer sb = new StringBuffer("BoardCategoryBean{");
        sb.append("category_id='").append(category_id).append('\'');
        sb.append(", category='").append(category_name).append('\'');
        sb.append(", regdate=").append(regdate);
        sb.append(", board_cnt=").append(board_cnt);
        sb.append(", seq=").append(seq);
        sb.append('}');
        return sb.toString();
    }
}
```
Lombok을 사용하면 아래의 코드와 같이 코드를 줄일 수 있다.<br>
클래스에 @Getter,@Setter,@ToString와 같은 어노테이션을 붙여주면 자동으로 생성해준다.
```java
import lombok.*;

@Getter
@Setter
@ToString
@NoArgsConstructor
@AllArgsConstructor

public class BoardCategoryLombok {

    private String category_id;

    private String category_name;

    private Date regdate;

    private int board_cnt;

    private int seq;

}
```
+ `@AllArgsConstructor` : @AllArgsConstructor는 모든 변수를 사용하는 생성자를 자동완성 시켜주는 어노테이션이다. 
+ `@NoArgsConstructor` : @NoArgsConstructor는 어떠한 변수도 사용하지 않는 기본 생성자를 자동완성 시켜주는 어노테이션이다.
+ `@EqualsAndHashCode` :  @EqualsAndHashCode는 클래스에 대한 equals 함수와 hashCode 함수를 자동으로 생성해준다. 
+ `@ToString` : @ToString 어노테이션을 활용하면 클래스의 변수들을 기반으로 ToString 메소드를 자동으로 완성시켜 준다.
+ `@Data` : @Data 어노테이션을 활용하면 @ToString, @EqualsAndHashCode, @Getter, @Setter, @RequiredArgsConstructor를 자동으로 완성시켜준다.
