### 분산 DB의 투명성 
지병위분장중

지역 사상 투명성 : 지역 DBMS와 물리적 DB사이의 사상이 보장
병행 투명성 : 다수의 트랜잭션을 동시해 수행했을 때 결과의 일관성이 유지됨
위치 투명성 : 사용하려는 데이터 저장장소를 노출하지 않아도 된다.
분할 투명성 : 하나의 논리적 관계가 분할되어 각 단편의 사본이 여러 사이트에 저장됨
장애 투명성 : 구성요소의 장애에 무관하게 트랜잭션의 원자성이 유지됨
중복 투명성 : db객체 중복 여부를 몰라도 됨