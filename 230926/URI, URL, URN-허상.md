### URI

- Uniform Resource Identifier, 통합 자원 식별자의 줄임말
- 인터넷의 자원을 식별할 수 있는 문자열
- URL과 URN은 URI의 하위개념
- URI라는 개념은 어떤 형식이 있다기 보다는 특정 자원을 식별하는 문자열을 의미. 그래서 URL이 아니고 URN도 아니면 그냥 URI

### URL
- Uniform Resource Locator의 줄임말
- 네트워크 상에서 리소스(웹 페이지, 이미지, 동영상 등의 파일) 위치한 정보를 나타낸다.
- HTTP 프로토콜 뿐만아니라 FTP, SMTP 등 다른 프로토콜에서도 사용할 수 있다
- 더 효율적으로 리소스에 접근하기 위해 클린한 URL 작성을 위한 방법론
###### 구조
`scheme:[//[user[:password]@]host[:port]][/path][?query][#fragment]`
1. scheme : 사용할 프로토콜을 뜻하며 웹에서는 http 또는 https를 사용
2. user와 password : (서버에 있는) 데이터에 접근하기 위한 사용자의 이름과 비밀번호
3. host와 port : 접근할 대상(서버)의 호스트명과 포트번호
4. path : 접근할 대상(서버)의 경로에 대한 상세 정보
5. query : 접근할 대상에 전달하는 추가적인 정보 (파라미터)
6. fragment : 메인 리소스 내에 존재하는 서브 리소스에 접근할 때 이를 식별하기 위한 정보

ex) http://127.0.0.1:8080/user/1?q=test

### URN
- Uniform Resource Name의 줄임말
- 이름으로 리소스를 특정하는 URI
- http와 같은 프로토콜을 제외하고 리소스의 이름을 가리키는데 사용
- 리소스 접근방법과, 웹 상의 위치가 표기되지 않는다.
- 실제 자원을 찾기 위해서는 URN을 URL로 변환하여 이용

### URL과 URN의 차이점
URL은 어떻게 리소스를 얻을 것이고 어디에서 가져와야하는지 명시하는 URI
URN은 리소스를 어떻게 접근할 것인지 명시하지 않고 경로와 리소스 자체를 특정하는 것을 목표로하는 URI