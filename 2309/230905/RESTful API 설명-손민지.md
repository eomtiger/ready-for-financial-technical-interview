# 간단한 답변
Restful API는 HTTP 통신을 REST 기반의 규칙을 잘 지켜서 설계된 API입니다.  
REST 설계 규칙은 **URI는 정보의 자원만 표현해야 하며, 자원의 행위는 HTTP Method(GET, POST, PUT, PATCH, DELETE)에 명시**하는 것을 말합니다.  

<br>
<br>

## 배경 지식

### REST
네트워크 상에서 Client와 Server 사이의 통신 방식 중 하나이다.  
REpresentational State Transfer의 약자로, 자원을 URI로 표시하고 해당 자원의 상태를 주고 받는 것을 의미한다.  
  
REST의 구성 요소
- 자원(Resource): URI
- 행위(Verb): HTTP Method(GET, POST, PUT, PATCH, DELETE)
- 표현(Representations) : Client와 Server가 데이터를 주고받는 형태로 JSON, XML, TEXT, RSS 등

즉, REST는 URI를 통해 자원을 표시하고, HTTP Method를 이용하여 해당 자원의 행위를 정해주며 그 결과를 받는 것을 말한다.  

---

### REST API
Rest 기반의 규칙들을 지켜서 설계된 API로,  
가장 큰 특징은 **각 요청이 어떤 동작이나 정보를 위한 것인지를 그 요청의 모습 자체로 추론이 가능**한 것이다.  

**REST API 설계 시 가장 중요한 항목**은 다음의 2가지로 요약합니다.
> 첫 번째, **URI는 정보의 자원을 표현**해야 한다. (행위(Method)는 URI에 포함하지 않는다.)  
> 두 번째, **자원에 대한 행위는 HTTP Method(GET, POST, PUT, PATCH, DELETE)로 표현**한다.  
  
**REST API의 설계 규칙**
1. URI는 명사를 사용한다. (리소스명은 동사가 아닌 명사를 사용해야 한다.)  
1-1. 아래와 같은 동사를 사용하지 말 것  
/getAllUsers  
/getUserById  
/createNewUser  
/updateUser  
/deleteUser

3. 슬래시( / )로 계층 관계를 표현한다.

4. URI 마지막 문자로 슬래시 ( / )를 포함하지 않는다.

5. 밑줄( _ )을 사용하지 않고, 하이픈( - )을 사용한다.

6. URI는 소문자로만 구성한다.

7. HTTP 응답 상태 코드 사용  
클라이언트는 해당 요청에 대한 실패, 처리완료 또는 잘못된 요청 등에 대한 피드백을 받아야 한다.

7. 파일확장자는 URI에 포함하지 않는다.  
Ex) http://dev-coco.tistory.com/restapi/220/photo.jpg (X)

---

### RESTful API
REST의 원리를 잘 따르는 시스템을 RESTful이란 용어로 지칭.  
REST를 REST답게 쓰기 위한 방법이지만 누군가가 공식적으로 발표한 것이 아니고 그저 개발자들이 비공식적으로 의견을 제시한 것이라 명확한 정의는 없다고 한다.
하지만 RESTful의 목적은 이해하기 쉽고 사용하기 쉬운 REST API를 만드는 것이다.  

Restful 하지 못한 경우  
- CRUD 기능을 전부 POST Method로만 처리하는 API  
- URI에 자원과 id 외 정보가 들어가는 경우  
