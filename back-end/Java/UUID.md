# UUID 란?
네트워크 상에서 교유성이 보장되는 id를 만들기 위한 표준 규약이다.
UUID는 Universally Uniqure IDentifier의 약어이고 범용 고유 식별자라고 한다.<br>
로컬에서 ID를 관리한다면 어떤 아이디들이 생성되었는지 확인한 후 중복을 체크하는 것이 가능하지만, 네트워크 상에서는 이야기가 다르다.



"중복되는 확률이 0에 가까운, 매우 낮은 확률을 가지는 ID를 만드는 방법" 이 방법이 바로 UUID이다. UUID는 계속 생성되어도 중복이 생길 가능성이 0에 가깝다.



# UUID의 구성
UUID는 8-4-4-4-12 형태의 문자이다. 각 문자는 16진수 숫자이며, 예를 들면 아래와 같은 형태이다.



`05474f5e-52fa-44a4-8a93-edf7e0634097`



각 부분에 대한 설명은 다음과 같다. HexDigits가 바로 8-4-4-4-12 형태인 것을 볼 수 있다.

![img](https://blog.kakaocdn.net/dn/sUfZJ/btsteNkBVEn/R00fA2RADM2kaTKvqblA7k/img.png)

### 시간을 기반으로 구성된 부분들 : time_low, time_mid, time_hi_and_version
time_low, time_mid, time_hi_and_version 필드는 UUID의 시간을 기반으로 구성된 부분을 나타낸다.

### clock_seq_hi_and_res, clock_seq_low 구성 방법
clock_seq_hi_and_res 와 clock_seq_low 는 버전마다 다른 값을 가지는데, Kotlin, Java에서 사용하는 UUID.random() 은

버전 4의 UUID가 사용되며 이는 난수를 기반으로 생성된다.



## UUID 충돌 확률
UUID는 중복되기 어려운 값들을 수없이 만듦으로써 단일 값을 보장한다. UUID가 충돌할 확률은 2의 122승 분의 1이며 이에 대한 충돌은 거의 불가능에 가깝다.



## Kotlin에서의 UUID
import java.util.UUID

val uuid = UUID.random()
println(uuid)

## Java에서의 UUID
```java
import java.util.UUID

UUID uuid = UUID.randomUUID();
System.out.println(uuid)
```

## UUID의 장점
기본키로 UUID를 사용할 경우 얻는 장점

UUID는 데이터에 대한 정보를 노출하지 않기 때문에 보안상 안전하다.
데이터베이스가 여러 개인 경우, 하나의 ID가 여러 데이터베이스에서도 고유한 값이라고 볼 수 있다.

## UUID의 단점
기본키로 UUID를 사용할 경우 얻는 단점

UUID는 기존의 increment pk 보다 더 많은 저장 장소를 필요로 한다.
테이블과 인덱스의 크기가 커지므로, DB의 디스크와 메모리를 많이 사용하게 된다.

## 언제 사용?
애플리케이션 내부용 키로는 자동증가 pk, 외부에 공개할 키로는 uuid를 사용하는 것을 권장한다.

자동증가 pk를 사용하게 되면 성능과 저장 장소 측면에서 이점이 있다.
식별값이 외부로 노출될 수 있는 서비스라면 UUID로 식별하는 것이 좋다.