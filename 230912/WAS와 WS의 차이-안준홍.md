# WAS와 WS의 차이
WAS는 동적인 컨텐츠를 처리하고 비즈니스 로직을 넣을 수 있지만 WS는 정적인 컨텐츠를 처리하고 비즈니스 로직을 넣을 수 없습니다.

<br>

## Web Server(WS)란?
- 웹 브라우저(클라이언트)로부터 HTTP 요청을 받아 HTML 문서와 같은 **정적 컨텐츠**를 제공하는 프로그램입니다.

```markdown
💡 정적 컨텐츠란?
- 요청 인자 값에 상관없이 달라지지 않는 컨텐츠(html, css, image...)
- 어느 사용자 요청이든 항상 동일한 컨텐츠
```

<br>

### Web Server의 기능 
- 클라이언트로부터 HTTP 요청을 받을 수 있습니다.
- 정적 컨텐츠를 요청 시
    - 정적 컨텐츠 제공
- 동적 컨텐츠 요청 시
    - Web Application Server(WAS)로 전달하여 WAS가 처리한 결과를 클라이언트에 전달합니다.

<br>

## Web Application Server(WAS)란?
- DB 조회나 다양한 비즈니스 로직 처리를 요구하는 **동적 컨텐츠**를 제공하기 위해 만들어진 프로그램입니다.
```markdown
💡 동적 컨텐츠란?
- 요청 인자에 따라 바뀔 수 있는 컨텐츠
```

<br>

### WAS의 기능
- 클라이언트로부터 HTTP 요청을 받을 수 있습니다.(대부분의 WAS는 Web Server 내장)
- 요청에 맞는 정적 컨텐츠(html, css, image...)를 제공할 수 있습니다.
- DB조회나 다양한 비즈니스 로직 처리를 통해 동적 컨텐츠를 제공할 수 있습니다.

<br>

### WS와 WAS를 같이 사용했을 때의 장점
- 책임 분할을 통한 서버 부하 방지
    - 정적 컨텐츠는 Web Server, 동적 컨텐츠는 WAS가 담당하도록 설정이 가능합니다.
- 여러 대의 WAS 로드밸런싱
    - WAS가 처리해야 하는 요청을 여러 WAS가 나누어서 처리할 수 있도록 설정이 가능합니다.
- 여러 대의 WAS Health Check
- 보안
    - 리버스 프록시를 통해 실제 서버를 외부에 노출하지 않을 수 있다.
```markdown
💡 Health Check란?
- 서버에 주기적을 HTTP 요청을 보내 서버의 상태를 확인하는 것입니다.(ex: 특정 url 요청에 200 응답이 오는지)
- Interval: health check를 통해 서버 상태를 확인하는 요청을 날리는 주기(default: 5초)
- Fails: 정해진 횟수만큼 연속으로 실패하면 서버가 비정상이라고 인지(default: 1회)
- Passes: 서버가 다시 복귀되어 요청이 정해진 횟수만큼 연속으로 성공하면 서버가 정상으로 인지(default: 1회)
```

---
### 참조
- https://www.youtube.com/watch?v=mcnJcjbfjrs&ab_channel=%EC%9A%B0%EC%95%84%ED%95%9C%ED%85%8C%ED%81%AC