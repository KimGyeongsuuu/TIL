# Token
클라이언트에서 인증 정보를 보관하는 방법이다.
토큰은 클라이언트에서 저장함으로 보안에 취약하다고 느낄 수 있지만, 토큰은 암호화되어서 클라이언트에 저장된다.

### JWT
Json Wep Token 의 약자로 웹에서 쓰이는 json 토큰이다.<br>
종류는 access token, refresh token 두가지다.

### Access Token & refresh token
AccessToken은 보호된 정보에 접근할 수 있는 권한을 부여하는 토큰이다.
사용자가 처음 인증을 받게 되면 accessToken, refreshToken을 부여받는데 실제로 권한을 얻는 토큰은 accessToken이다.<br>

자신이 해당 페이지에 대한 권한을 받고 싶다면 accessToken만 있으면 된다.
만약 해커가 자신의 accessToken을 탈취한다면 해커들이 나쁘게 사용할 수도 있다.

그래서 accessToken의 유효시간을 짧게 주고 오랫동안 사용할 수 없도록 한다.
accessToken의 유효시간이 다하면 그때 refreshToken을 활용해서 accessToken을 재발급받는다.

**그래서 access token은 로그인 정보에 접근할 수 있는 카드키, refresh token은 카드키 재발급**이라고 생각하면 기억하기 편할 것이다.

유저의 편의보다 정보로 지키는 것이 더 중요한 웹사이트들은 refresh token을 사용하지 않는 곳도 있다. 그러면 유저는 일정주기 마다 새로 로그인을 해야 할 것이다.


### 토큰기반 인증의 장점
+ 서버가 클라이언트에 대한 정보를 저장할 필요가 없다
+ 클라이언트가 새로운 요청을 보낼때마다 헤더에 토큰과 함께 요청하면 된다
+ 안전하다
+ 권한부여하기에 편리하다

### JWT를 이용한 인증 과정

![JWT](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FddMTy5%2Fbtq4X5CPaYg%2FVUNZoHe45R0kj33ntKG1r0%2Fimg.png)

1. 사용자가 로그인을 하면 회원DB에서 사용자 확인을 한다.
2. 사용자 확인이 되면 AccessToken과 RefreshToken을 발급한다.
3. 클라이언트가 요청을 할 때 헤더에 AccessToken과 함께 데이터를 요청한다.
4. 서버에서 AccessToken을 검증하고 일치하면 요청 데이터를 응답한다.
5. AccessToken이 만료가 되면 서버에서 AccessToken 만료 신호를 클라이언트로 보낸다.
6. 클라이언트가 AccessToken 재발급요청을 서버로 요청한다.
7. AccessToken에 해당하는 RefreshToken을 확인하고 새로운 AccessToken을 발급한다.
8. 클라이언트는 새로운 AccessToken으로 데이터를 요청한다.




