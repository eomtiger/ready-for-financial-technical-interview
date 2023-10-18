# ORM
Object-Relational Mapping 즉, **객체와 관계형 데이터베이스 매핑**의 줄임말입니다.  
우리가 OOP(Object Oriented Programming)에서 쓰는 객체라는 개념을 구현한 클래스와  
RDB(Relational DataBase)에서 쓰이는 데이터인 테이블을 매핑(연결)하는 것을 의미합니다.  

ORM을 이용하면 **SQL Query가 아닌 직관적인 코드(메소드)로서 데이터를 조작**할 수 있습니다.  
예를들어, Member 테이블의 데이터를 출력하기 위해서 MySQL에서는 SELECT * FROM Member; 라는 query를 실행해야 하지만,  
ORM을 사용하면 Member 테이블과 매핑된 객체를 member라 할 때, member.findAll(); 라는 메소드 호출로 데이터 조회가 가능합니다.  

<br>

**ORM 장점**
- 객체지향적인 코드로 인해 더 직관적이고 로직에 집중할 수 있도록 도와준다.
- 재사용 및 유지보수의 편리성이 증가한다.
- DBMS(Database Management System)에 대한 종속성이 줄어든다.

<br>

**ORM 단점**
- 완벽한 ORM으로만 서비스를 구현하기는 어렵다.
- 프로시저가 많은 시스템에선 ORM의 객체 지향적인 장점을 활용하기 어렵다.

<br>
<br>

### 더 많은 내용
https://dev-coco.tistory.com/73
