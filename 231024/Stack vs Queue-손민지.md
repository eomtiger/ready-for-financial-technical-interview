# Stack vs Queue
## 공통점
- 선형 구조(Linear Structure)의 형태  
  데이터를 저장하기 위한 기본적인 형태로 데이터가 '일렬로 나열'되어 있을 뿐만 아니라 데이터 간에 순서가 있고 논리적으로 이어져 있는 구조를 의미
<br>

## 차이점
**Stack(스택)**  
- 후입선출(LIFO, Last-In-First-Out) : 가장 마지막에 추가된 데이터가 가장 먼저 삭제
- Java에서 스택은 java.util.Stack 클래스를 이용해 구현
- 사용 예시 : 함수 호출, 수식 계산, 웹 브라우저 방문 기록, 웹브라우저의 뒤로/앞으로 같은 기능 등

**Queue(큐)**  
- 선입선출(FIFO, First-In-First-Out) : 가장 먼저 추가된 데이터가 가장 먼저 삭제
- Java에서 큐는 인터페이스의 역할을 수행하며 ArrayDeque, LinkedList, PriorityQueue 등을 통해서 구현체를 구현
- 사용 예시 : 최근 사용 문서, 인쇄 작업 대기목록, CPU 스케줄링, 너비 우선 탐색, 캐시 등
<br>
<br>

### 더 많은 내용
https://adjh54.tistory.com/135
