# JWT (JSON Web Token)
- JSON 포맷을 이용하는 Claim 기반의 웹 토큰
- 토큰 자체를 정보로 사용하는 Self-Contained 방식으로 정보를 전달
- 헤더(Header).내용(Payload).서명(Signature)으로 구성되며 각 파트를 점(.)으로 구분
  - 헤더(Header) : 토큰의 타입과 해시 암호화 알고리즘(방식지정)으로 이루어져 있음
  - 내용(Payload) : 토큰에 사용자가 담고자 하는 정보를 담음. 내용에는 Claim이 담겨있고, JSON(Key/Value)형태의 한 쌍으로 이루어져 있음
  - 서명(Signature) : 토큰을 인코딩하거나 유효성 검증할 때 사용하는 고유한 암호화 코드. 헤더와 내용의 값을 인코딩한다.


### 더 많은 내용
- https://dev-coco.tistory.com/103  
- https://inpa.tistory.com/entry/WEB-%F0%9F%93%9A-JWTjson-web-token-%EB%9E%80-%F0%9F%92%AF-%EC%A0%95%EB%A6%AC
