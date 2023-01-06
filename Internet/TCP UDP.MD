# TCP/UDP
TCP와UDP는 OSI 7 계층 중 전송계층에서 사용되는 프로토콜이다.<br>
전송계층은 프로토콜 내에서 수신자와 송신자를 연결하는 통신 서비스를 제공하는 계층인데,
IP에 의해 전달되는 패킷의 오류를 검사하고 재전송 요구 등의 제어를 담당한다.<br>
이러한 전송계층에서 사용되는 프로토콜이 `TCP/UDP`입니다.

![TCP/UDP](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FMXeVk%2FbtrlAsb95n7%2FUIgKKI5lhIvpb3YfPxQhf0%2Fimg.jpg)

### TCP(Transmission Control Protocol)
TCP는 신뢰성있는 데이터를 전송하는 연결 지향형 프로토콜 입니다. 일반적으로 TCP와 IP가 많이 사용되는데, IP가 데이터의 전송을 처리했다면 TCP는 패킷 추적 및 관리를 처리합니다.
연결 지향형인 TCP는 3-way handshaking이라는 과정을 통해 연결하고 통신을 시작하는데, 흐름제어와 혼잡제어를 제공하여 데이터의 순서를 보장합니다.

+ 흐름제어 : 보내는 측과 받는 측의 데이터 처리속도 차이를 조절해주는 것
+ 혼잡제어 : 네트워크 내의 패킷 수가 넘치게 증가하지 않도록 방지하는 것

**특징**
+ 연결형 서비스로 가산 회선 방식을 제공
+ 데이터의 전송 순서를 보장
+ 데이터의 경계를 구분하지 않음
+ 신뢰성있는 데이터 전송
+ UDP보다 전송이 느리다
+ 연결을 설정(3-way handshaking)과 해재(4=way handshaking)


### UDP(User Datagram Protocol)
UDP는 비연결형 프로토콜로써, 인터넷상에서 서로 정보를 주고 받을때 정보를 보낸다는 신호나 받는다는 신호 없이 일반적으로 데이터를 통신하는 방법입니다.<br>
TCP와 다르게 연결 설정이 없으면 TCP보다 전송속도도 빠릅니다.

**툭장**
+ 비연결형 서비스로 데이터그램 방식을 제공
+ 비신뢰성
+ 혼잡제어를 하지 않기에 TCP보다 빠르다
+ TCP의 handshaking같은 연결 설정이 없다


### 요약
TCP는 연속적인 신뢰성 있는 전송이 중요할 때 사용되는 프로토콜이며, UDP는 TCP보다 빠르고 네트워크 부하가 적다는 장점이 있지만 신뢰성 있는 데이터 전송을 보장하지 않는다.
그렇기때문에 신뢰성보다는 빠른 전송이 필요한 서비스에서는 UDP가 많이 사용됩니다.

![img](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2F0E71C%2FbtrlA7FPUnj%2FsC9ZwQKWS6G5st0KtJwrK0%2Fimg.png)