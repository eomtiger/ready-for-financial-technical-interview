# JPA, JDBC, MyBatis

### JDBC
> Java에서 DB를 다루는 가장 기본적인 방식
- DB 접근, SQL을 날리게 할 수 있는 표준 API입니다.
- Java의 DB 접근 기술의 근간으로 모든 **Persistence Framework**는 내부적으로 JDBC API를 사용합니다.
- **Low-level API**로, 데이터베이스와의 직접적인 상호 작용이 필요한 경우에 적합합니다.

<br>

### JPA
> **Persistence Framework** 중 하나로, Persistence Layer에서 JDBC 프로그래밍의 복잠함 없이 간단하게 DB가 연동되는 시스템 개발 및 안정적인 구동을 보장하는 프레임워크 입니다.
- JDBC는 DB 연결을 위한 cennection 할당, 종료같은 부수적인 코드가 증가하게 되는데 이러한 복잡성을 줄인 것이 **Persistence Framework**입니다.

<br>

### MyBatis
> SQL Mapper 중 하나로, SQL을 직접 작성하고 매핑 관계를 정의하기 때문에 세밀한 제어가 가능하며, 기존 SQL 쿼리를 재활용할 수 있습니다.
- 객체와 SQL문을 매핑합니다.
- 내부에 JDBC를 사용합니다.
- 복잡한 쿼리를 짜는데 적합합니다.
- 간단한 CRUD 쿼리도 모두 작성해야 하는 단점이 존재합니다.
- 저장 프로시저 호출에 유용하며, 동적 쿼리 작성이나 매핑 로직 수정에 편리합니다.
- SQL을 직접 작성하고 매핑 관계를 설정하며, 데이터베이스 연결 및 트랜잭션 관리는 프레임워크가 처리합니다.

<br>

---

<br>

### 참조
- [JDBC vs MyBatis vs JPA, Hibernate 차이](https://www.acmicpc.net/problem/3184)
- [JDBC, JPA, MyBatis? | Java와 DB 간 API 정리](https://freedman.tistory.com/99)