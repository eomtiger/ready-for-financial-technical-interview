# Error와 Exception

프로그램이 실행 중 어떤 원인에 의해서 **오작동을 하거나 비정상적으로 종료**되는 경우를 프로그램 오류라 하고,  
프로그램 오류에는 에러(error)와 예외(exception) 두 가지로 구분할 수 있습니다.

<br>

**Error (에러)**
- 메모리 부족이나 스택오버플로우와 같이 발생하면 복구할 수 없는 심각한 오류
- 시스템 레벨에서 발생하여, 개발자가 어떻게 조치할 수 없는 수준을 의미
- Error의 상황을 미연에 방지하기 위해서 Exception 상황을 만들 수 있음

<br>

**Exception (예외)**
- 발생하더라도 수습할 수 있는 비교적 덜 심각한 오류
- 프로그래머가 적절히 코드를 작성해주면 비정상적인 종료를 막을 수 있음
- Exception Handling  
  JAVA에서 모든 예외가 발생하면 (XXX)Exception 객체를 생성  
  예외를 처리하는 방법 크게 2가지
	- try ~ catch를 이용해서 예외에 대한 최종적인 책임을 지고 처리하는 방식
	- throws Exception을 이용해서 발생한 예외의 책임을 호출하는 쪽이 지도록 하는 방식

<br>
<br>

### 더 많은 내용
https://gyoogle.dev/blog/computer-language/Java/Error%20&%20Exception.html  
https://choiblack.tistory.com/39
