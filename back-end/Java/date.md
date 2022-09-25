# date
java에서 현재 시간을 알기 위해서는 Date 객체를 사용합니다.
```java
import java.util.Date; public class CurrentTime{   
    public static void main(String[] args){    
        Date today = new Date();    System.out.println(today);  
    } 
}
```
결과

```
Mon Dec 25 22:05:02 KST 2017
```

# Calendar
Date가 가지는  단점을 해결하고 등장한 것이 Calendar클래스

+ Calendar 클래스 생생 방법
+ Calendar클래스는 인터페이스로 정의된 추상클래스이다.
+ Calendar클래스에 대한 인스턴스를 생성하려면 Calendar가 가지고 있는 클래스 메소드 getInstnace()를 사용해야 한다.
+ getInstance()메소드를 호출하면 내부적으로 java.util.+ GregorianCalendar 인스턴스를 만들어서 리턴한다.
+ GregorianCalendar는 Calendar의 자식 클래스이다. (음력, 유대력 등등 다양한 달력이 존재)
```java
Calendar cal = Calendar.getInstance();
```
```java
// 현재날짜에 원하는 만큼 연산이 가능
cal.add(Calendar.MONTH, 1);

// Date 객체에 담아 형식지정이 가능
date = cal.getTime();
System.out.println(new SimpleDateFormat("yyyy-MM-dd").format(date))
```