# OAuth란?
> 웹 이용 시 비밀번호를 제공하지 않고 다른 웹 사이트 상의 자신의 정보에 대해 접근 권한을 부여할 수 있는 수단으로 사용되는 개방형 표준 기술입니다.  
간단히 말하자면, **어플리케이션 이용 시 ID와 PW를 신뢰할 수 있는 다른 어플리케이션을 통해 대신 제공해 인증 과정을 처리하는 방식입니다**.

<br>

### OAuth 인증 방식
1. 사용자가 서비스에게 서비스 접근 및 로그인 요청
2. 서비스가 인증 서비스(Authorization Server)에 사용자 대신 로그인 요청
3. 인증 서비스가 사용자에게 로그인 페이지 제공
4. 사용자가 ID, PW를 입력하여 인증 서비스에 요청하여 유효성 확인
5. 유효성이 확인되면, 인증 서비스에서 사용자에게 인증 코드(Authorization Code) 발급
6. 사용자가 서비스에게 Redirect Callback URL로 발급받은 인증 코드를 담아서 요청
7. 서비스가 사용자가 전달한 인증 코드를 사용해 인증 서비스에 인증 요청
8. 인증 서비스에서 해당 인증 코드를 검증 후 인증 및 서비스에서 발급된 Access Token & Refresh Token 저장
9. 서비스에서 사용자의 인증 완료 & 로그인 처리
-> 이후 발급받은 Access Token을 사용해 컨텐츠 제공 서버(Resource Server)로부터 사용자의 정보를 요청하여 응답 받을 수 있습니다.
10. Refresh Token을 사용해 만료된 Access Token 대신 새로운 Access Token을 재발급 받고 해당 Access Token으로 로그인 상태를 유지해 자동 로그인 상태를 유지합니다.

<br>

---

### 참조
- https://medium.com/cean-logs/sso%EC%99%80-%EC%86%8C%EC%85%9C-%EB%A1%9C%EA%B7%B8%EC%9D%B8-7abbbdc62acb
- https://ksh-coding.tistory.com/62