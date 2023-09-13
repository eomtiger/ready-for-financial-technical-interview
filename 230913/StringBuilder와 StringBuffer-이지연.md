# StringBuilder와 StringBuffer의 차이는?

우선, StringBuilder와 StrinbBuffer 모두 **변경 가능한 문자열**을 생성하며, append() 등의 **api를 지원**합니다.   

둘의 차이점은 다음과 같습니다. **StringBuilder**는 동기화를 지원하지 않아 싱글 스레드에서 속도가 빠릅니다. 반면에 **StringBuffer**는 멀티 스레드 환경에서의 동기화를 지원합니다.

# 배경 지식

### String

- Immutable(불변)
- String 문자열을 연산하는 과정에서 불변 객체의 반복 생성으로 퍼포먼스가 낮아짐

**Immutable**

- 객체 수정 불가능
- 수정이 필요한 경우, 새로운 객체를 생성하여 재할당

**→ String의 단점을 보완한 StringBuilder와 StringBuffer**

→ **mutation (변경 가능한 문자열 생성)**

### StringBuilder

- 버퍼(buffer: 데이터를 임시로 저장하는 메모리)에 문자열 저장
- 버퍼 내부에서 추가, 수정, 삭제 작업 가능
- 단일 스레드 환경에서 사용

### StringBuffer

- 버퍼(buffer: 데이터를 임시로 저장하는 메모리)에 문자열 저장
- 버퍼 내부에서 추가, 수정, 삭제 작업 가능
- 멀티 스레드 환경에서 사용
