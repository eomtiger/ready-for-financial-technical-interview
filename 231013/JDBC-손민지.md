# JDBC(Java Database Connectivity)
Java 기반 애플리케이션의 데이터를 데이터베이스에 저장 및 업데이트하거나, 데이터베이스에 저장된 데이터를 Java에서 사용할 수 있도록 하는 Java API입니다.
**Java와 DBMS간의 통신을 중간에서 번역**해주는 역할을 합니다.  
JDBC는 Java 애플리케이션 내에서 JDBC API를 사용하여 데이터베이스에 접근하는 단순한 구조입니다.  
JDBC API를 사용하기 위해서는 **JDBC 드라이버*를 먼저 로딩한 후 데이터베이스와 연결**하게 됩니다.
<br>

> ***JDBC 드라이버**  
> 데이터베이스와의 통신을 담당하는 인터페이스  
> Oracle, MS SQL, MySQL 등과 같은 데이터베이스에 알맞은 JDBC 드라이버를 구현하여 제공  
> JDBC 드라이버의 구현체를 이용해서 특정 벤더의 데이터베이스에 접근할 수 있음  
<br>

**JDBC 표준 인터페이스**
- Connection - 연결
- Statement - SQL을 담은 내용
- ResultSet - SQL 요청 응답
 <br>

**JDBC API의 구성 요소들의 동작 흐름**
1. JDBC 드라이버 로딩 : 사용하고자 하는 JDBC 드라이버를 로딩. JDBC 드라이버는 DriverManager 클래스를 통해 로딩.
2. Connection 객체 생성 : JDBC 드라이버가 정상적으로 로딩되면 DriverManager를 통해 데이터베이스와 연결되는 세션(Session)인 Connection 객체를 생성.
3. Statement 객체 생성 : Statement 객체는 작성된 SQL 쿼리문을 실행하기 위한 객체로 정적 SQL 쿼리 문자열을 입력으로 가짐.
4. Query 실행 : 생성된 Statement 객체를 이용하여 입력한 SQL 쿼리를 실행.
5. ResultSet 객체로부터 데이터 조회 : 실행된 SQL 쿼리문에 대한 결과 데이터 셋.
6. ResultSet, Statement, Connection 객체들의 Close : JDBC API를 통해 사용된 객체들은 생성된 객체들을 사용한 순서의 역순으로 Close.
