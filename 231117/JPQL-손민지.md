# JPQL(Java Persistence Query Language)
JPA가 지원하는 다양한 쿼리 기술 중 하나로, 엔티티(객체)를 조회하는 객체지향 쿼리 언어이다.  
JPA에서 제공하는 메소드 호출만으로는 섬세한 쿼리 작성이 어렵다는 문제에서 JPQL이 탄생했다.  

### JPQL 특징
- 테이블이 아닌 객체를 검색하는 객체지향 쿼리
- SQL과 비슷한 문법을 가짐
- SQL을 추상화 했기 때문에 특정 벤더에 종속적이지 않음
- JPA는 JPQL을 분석하여 SQL을 생성한 후 DB에서 조회

### SQL과 다른 점
```java
// 기본 문법 예시
String jpql = "select m from Member as m where m.name = 'coco'";
```

- 대소문자 구분
> 엔티티와 속성은 대소문자를 구분한다.  
> 엔티티 이름인 Member, 그리고 Member의 속성 name은 대소문자를 구분해줘야 한다.  
> 반면에 SELECT, FROM, AS 같은 JPQL 키워드는 대소문자를 구분하지 않아도 된다.

- 엔티티 이름
> JPQL에서 사용한 Member는 클래스 이름이 아닌 엔티티 이름이다. 엔티티 이름은 @Entity(name="abcd")로 설정 가능하다.
> name 속성을 생략하면 기본 값으로 클래스 이름을 사용한다.
 
- 별칭
> JPQL에서 엔티티의 별칭은 필수적으로 명시해야 한다.
> 별칭을 명시하는 AS 키워드는 생략할 수 있다.

<br>

### 참고
https://dev-coco.tistory.com/141
