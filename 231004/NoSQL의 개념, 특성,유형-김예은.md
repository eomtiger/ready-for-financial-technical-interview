### NoSQL의 개념

- 전통적인 RDBMS와 다른 DBMS를 지칭하기 위한 용어로 데이터 저장에 고정된 테이블 스키마가 필요하지않고, 조인 연산을 사용할 수 없으며, 수평적으로 확장이 가능한 DBMS다.

### 특성

- BASE
- Basically Available : 언제든지 데이터는 접근 가능, 분산시스템이기에 항상 가용성 중시
- Soft-State : 노드에 상태는 외부에서 전송된 정보를 통해 결정, 특정 시점에서는 데이터의 일관성이 보장안됨
- Eventually Consistency : 일정시간이 지나면 데이터 일관성 유지, 일관성 중시 및 지향

### 유형

- Key-Value Store : 유니크한 키에 하나의 밸류를 가지고 있는 형태 (redis , Dynamo)
- Column Family Data Store : Key안에 (Column, Value) 조합으로 된 여러 개의 필드를 갖는 DB (카산드라)
- Document Store : Value의 데이터 타입이 Document라는 타입을 사용하는 DB, 복잡한 계층 구조 표현 가능 (몽고DB)
- Graph Store : 시맨팁 웹과 온톨로지 분야에서 활용되는 그래프로 데이터를 표현하는 DB(Neo4j, AllegroGraph)
