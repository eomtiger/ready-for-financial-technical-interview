# JPQL, Querydsl

JPA는 정적인 상황에서 사용하는걸 권장하기 때문에 복잡한 쿼리와 동적인 쿼리에 대해서는 문제가 발생하게 되는데, 이럴 때 JPQL과 Querydsl을 사용할 것을 권장하고 있습니다.

<br>

---
<br>

## JPQL
JPQL은 JPA의 일부로 Query를 Table이 아닌 Entity(객체) 기준으로 작성하는 **객체지향 쿼리 언어**라고 정의할 수 있습니다.

JPQL은 객체를 기준으로 모든 것이 움직이기 때문에 개발할 때, Table에 매핑되는 객체가 반드시 존재해야 하며 당연하게도 검색할 때도 Table이 아닌 객체를 대상으로 검색해야 합니다.

### JPQL 특징
1. SQL을 추상화한 JPA의 객체지향 쿼리
2. Table이 아닌 Entity 객체를 대상으로 개발
3. Entity와 속성은 대소문자 구분
4. 별칭(alias) 사용 필수

### JPQL 구현 방식
1. Entity Manager 활용
```Java
@Autowired
EntityManager em;

Person person = new Person();
Person.setFirstName("Junhong");
Prseon.setLastName("Ahn");
userRepository.save(person);

TypedQuery<User> tq = em.createQuery("select p from Person p where p.FirstName = :firstName and p.lastName = :lastName", Person.class);
tq.setParameter("firstName", "Junhong");
tq.setParameter("lastName", "Ahn");

List<Person> personList = tq.getResultList();
```

2. repository interface 활용
```Java
public interface PersonRepository extends JpaRepository<Person, Long>{
    
    /*	변수 바인딩 시, ?시퀀스 사용하는 경우 */
   @Query("select p from Person p where p.firstName = ?1 and p.lastName = ?2")
   Person findPerson(String firstName, String lastName);
   
   /*	변수 바인딩 시, :이름 사용하는 경우 */
   @Query("select p from Person p where p.firstName = :firstName and p.lastName = :lastName")
   Person findPerson2(@Param("firstName") String firstName, @Param("lastName") String lastName); 
}
```

### JPQL의 문제점
- JPQL은 문자열(=String) 형태 이기 때문에 개발자 의존적 형태
- Compile 단계에서 Type-Check가 불가능
- RunTime 단계에서 오류 발견 가능(장애 risk 상승)


<br>

---

<br>

## Querydsl
정적 타입을 이용해서 SQL, JPQL을 코드로 작성할 수 있도록 도와주는 오픈소스 빌더 API입니다.

기존 방식은 모두 문자열 형태로 쿼리가 작성되었고 이로 인해 Compile 단계에서 Type-Check가 불가했습니다. 이러한 risk를 줄이기 위해서 Querydsl이 등장했고 이를 통해 Compile 단계에서 Type-Check가 가능해졌습니다.

### Querydsl 구현 방식
```java
@PersistenceContext
EntityManager em;
 
public List<Person> selectPersonByNm(String firstNm, String lastNm){
	JPAQueryFactory jqf = new JPAQueryFactory(em);
	QPerson person = QPerson.person;
  
	List<Person> personList = jpf
								.selectFrom(person)
								.where(person.firstName.eq(firstNm)
									.and(person.lastName.eq(lastNm))
								.fetch();
                                
	return personList;
}

```

### Querydsl 특징
- 문자가 아닌 코드로 작성
- Compile 단계에서 문법 오류를 확인 가능
- 코드 자동 완성 기능 활용 가능
- 동적 쿼리 구현 가능
- 코드 라인 수가 길어짐

<br>

---

### 참조
- https://velog.io/@cho876/JPQL-vs-query-DSL