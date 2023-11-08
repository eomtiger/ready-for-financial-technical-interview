# Entity, DAO, BO, DTO, VO
DB 로직과 비즈니스 로직을 분리하고 효율적으로 데이터를 처리하기 위해서 각각의 객체를 나눔

## Entity
- DB의 테이블과 1대 1로 매핑되는 클래스
- DB의 테이블내에 존재하는 컬럼만을 속성(필드)으로 가져야 함

## DAO (Data Access Object)
- DB의 데이터에 접근하는 객체
- Repository 또는 Mapper에 해당

## BO (Business Object) 
- 여러 DAO를 활용해 비즈니스 로직을 처리하는 객체
- Service에 해당

## DTO (Data Transfer Object)
- 각 계층간의 데이터 교환을 위한 객체 (ex. View <- (DTO) -> Controller <- (DTO) -> Service)
- 주로 비동기 처리를 할 때 사용
- 로직을 갖고 있지 않는 순수한 데이터 객체
- getter/setter 메소드만을 가짐
- DB와 View 사이의 역할을 철저히 분리하기 위해서 Entity와 DTO를 분리해서 관리해야 함 

## VO (Value Object)
- 변하지 않는 데이터 객체
- 오직 read만 가능하며 getter만 가능해야 함
- 데이터가 불변이어야 하고, 단순히 저장된 값을 불러와야 하는 경우 사용

<br>

### 더 많은 내용
https://dev-coco.tistory.com/87
