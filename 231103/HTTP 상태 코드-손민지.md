# HTTP 상태 코드
- 상태 코드는 세 자리 숫자로 되어 있음
- 첫 번째 숫자는 HTTP 응답의 종류를 구분
- 나머지 2개의 숫자는 세부적인 응답 내용 구분
- 현재 100~500번 대까지 상태 코드가 정의되어 있음
- 첫 번째 자리 숫자에 따라 5가지로 분류해서 사용

### 1XX: Informational(정보 제공)
임시 응답으로 현재 클라이언트의 요청까지는 처리되었으니 계속 진행하라는 의미 (HTTP 1.1 버전부터 추가됨)

### 2XX: Success(성공)
클라이언트의 요청이 서버에서 성공적으로 처리되었다는 의미  
|상태코드|이름|의미|
|:---:|:---:|:---:|
|200|OK|요청 성공(GET)|
|201|Create|생성 성공(POST)|
|202|Accepted|요청 접수O, 리소스 처리X|
|204|No Contents|요청 성공O, 내용 없음|

### 3XX: Redirection(리다이렉션)
완전한 처리를 위해서 추가 동작이 필요한 경우. 주로 서버의 주소 또는 요청한 URI의 웹 문서가 이동되었으니 그 주소로 다시 시도하라는 의미  
|상태코드|이름|의미|
|:---:|:---:|:---:|
|300|Multiple Choice|요청 URI에 여러 리소스가 존재|
|301|Move Permanently|요청 URI가 새 위치로 옮겨감|
|304|Not Modified|요청 URI의 내용이 변경X|


### 4XX: Client Error(클라이언트 에러)
없는 페이지를 요청하는 등 클라이언트의 요청 메시지 내용이 잘못된 경우를 의미  
|상태코드|이름|의미|
|:---:|:---:|:---:|
|400|Bad Request|API에서 정의되지 않은 요청 들어옴|
|401|Unauthorized|인증 오류|
|403|Forbidden|권한 밖의 접근 시도|
|404|Not Found|요청 URI에 대한 리소스 존재X|
|405|Method Not Allowed	|API에서 정의되지 않은 메소드 호출|
|406|Not Acceptable|처리 불가|
|408|Request Timeout	|요청 대기 시간 초과|
|409|Conflict	|모순|
|429|Too Many Request|요청 횟수 상한 초과|

### 5XX: Server Error(서버 에러)
서버 사정으로 메시지 처리에 문제가 발생한 경우. 서버의 부하, DB 처리 과정 오류, 서버에서 익셉션이 발생하는 경우를 의미  
|상태코드|이름|의미|
|:---:|:---:|:---:|
|500|Internal Server Error|서버 내부 오류|
|502|Bad Gateway|게이트웨이 오류|
|503|	Service Unavailable|서비스 이용 불가|
|504|	Gateway Timeout|게이트웨이 시간 초과|
