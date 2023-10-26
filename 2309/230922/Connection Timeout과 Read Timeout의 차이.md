# Connection Timeout과 Read Timeout의 차이
### Connection Timeout
> 클라이언트가 정해진 시간까지 커넥션 수락이 오지 않아서 발생하는 Timeout을 Connection Timeout이라고 합니다.
-> 즉, **접근을 시도하는 시간 제한**이 Connection Timeout

<br>

### Read Timeout
> 클라이언트가 커넥션 수락을 받은 후 서버로 요청한 정보를 설정한 시간까지 응답을 주지 못해서 발생하는 Timeout을 Read Timeout이라고 합니다.
-> 즉, **접근 후 응답 시간 제한**이 Read Timeout