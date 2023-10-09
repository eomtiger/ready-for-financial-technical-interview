# JWT
> JSON Web Token의 약자로 인증에 필요한 정보들을 암호화시킨 JSON 토큰을 의미합니다. 그리고 JWT 기반 인증은 JWT 토큰(Access Token)을 HTTP 헤더에 실어 서버가 클라이언트를 식별하는 방식입니다.

<br>

---
### JWT 구조
> JWT는 .을 구분자로 나누어지는 세 가지 문자열의 조합입니다.
.을 기준으로 좌측부터 Header, Payload, Signature를 의미합니다.
- Header : HWT에서 사용할 타입과 해시 알고리즘의 종류
- Payload : 서버에서 첨부한 사용자 권한 정보와 데이터
- Signature : Header, Payload를 Base64 URL-safe Encode를 한 이후 Header에 명시된 해시함수를 적용하고, 개인키(Private Key)로 서명한 전자서명

<br>

### JWT 인증과정
1. 사용자가 ID, PW를 입력하여 서버에 로그인 인증을 요청합니다.
2. 서버에서 클라이언트로부터 인증 요청을 받으면 Header, Payload, Signature를 정의하고 이를 각각 Base64로 암호화하여 JWT를 생성하고 이를 쿠키에 담아 클라이언트에게 발급합니다.
3. 클라이언트는 서버로부터 받은 JWT를 로컬 스토리지에 저장합니다.(API를 서버에 요청할 때 Authorization header에 Access Token을 담아서 보냅니다.)
4. 서버는 클라이언트가 Header에 담아서 보낸 JWT가 서버에서 발행한 토큰인지 일치 여부를 확인하여 일치한다면 통과시켜줍니다.
5. 클라이언트가 보낸 Access Token이 만료했다면 클라이언트는 Refresh Token을 이용해서 서버로부터 새로운 Access Token을 발급 받습니다.
```markdown
**Access Token**
클라이언트가 갖고 있는 실제 유저 정보가 담긴 토큰입니다.
**Refresh Token**
만료된 Access Token을 재발급하기 위해 사용하는 토큰입니다.
```

<br>

### JWT vs Cookie & Session

| | 장점 | 단점 |
| --- | --- | --- |
| Cookie & Session | - Cookie만 사용하는 방식보다 보안 향상 <br> - 서버 쪽에서 Session 통제 가능 <br> - 네트워크 부하 낮음 | - 세션 저장소 사용으로 인한 서버 부하
| JWT | - 인증을 위한 별도의 저장소가 필요 없음 <br> - 별도의 I/O 작업 없는 빠른 인증 처리 <br> - 확장성이 우수함 | - 토큰의 길이가 늘어날수록 네트워크 부하 <br> - 특정 토큰을 강제로 만료시키기 어려움

<br>

### JWT 장점
- Header와 Payload를 가지고 Signature를 생성하므로 데이터 위변조를 막을 수 있습니다.
- 인증 정보에 대한 별도의 저장소가 필요없습니다
- JWT는 토큰에 대한 기본 정보와 전달할 정보 및 토큰이 검증됐음을 증명하는 서명 등 필요한 모든 정보를 자체적으로 지니고 있습니다.
- 클라이언트 인증 정보를 저장하는 세션과 다르게, 서버는 무상태(Stateless)가 되어 서버 확장성이 우수해질 수 있습니다.
- 토큰 기반으로 다른 로그인 시스템에 접근 및 권한 공유가 가능합니다.(쿠키와의 차이)
- OAuth의 경우 Facebook, Google 등 소셜 계정을 이용하여 다른 웹서비스에서도 로그인을 할 수 있습니다.
- 모바일 어플리케이션 환경에서도 잘 동작합니다.(모바일은 세션 사용 불가능)

### JWT 단점
- Self-Contained : 토큰 자체에 정보를 담고 있어 양날의 검이 될 수 있습니다.
- 토큰 길이 : 토큰의 Payload에 3종류의 클레임을 저장하기 때문에, 정보가 많아질수록 토큰의 길이가 늘어나 네트워크에 부하를 줄 수 있습니다.
- Payload 인코딩 : Payload 자체는 암호화 된 것이 아니라 Base64로 인코딩 된 것이기 때문에, 중간에 Payload를 탈취하여 디코딩하면 데이터를 볼 수 있으므로, Payload에 중요 데이터를 넣지 않아야 합니다.
- Store Token : Stateless 특징을 가지기 때문에, 토큰은 클라이언트 측에서 관리하고 저장합니다. 때문에 토큰 자체를 탈취당하면 대처하기가 어렵게 됩니다.

---
### 참조
- https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-JWTjson-web-token-%EB%9E%80-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC