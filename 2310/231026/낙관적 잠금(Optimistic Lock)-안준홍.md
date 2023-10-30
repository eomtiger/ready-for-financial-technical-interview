# 낙관적 잠금이란?
데이터 갱신시 충돌이 발생하지 않을 것이라고 낙관적으로 보고 잠금을 거는 기법입니다. DB 트랜잭션을 이용하지 않고 어플리케이션 레벨에서 `@Version` 어노테이션을 통해 지원하는 락으로, 이는 충돌 방지에 가깝다고 볼 수 있습니다.

<br>

---

<br>

# Lock 이란?

![Untitled](https://github.com/junhong625/TIL/assets/83000975/89955daa-0c5f-4e76-b1aa-45ddae3f290a)

사진과 같이 동시에 여러 connection에서 Data에 접근할 때 데이터들의 값들이 connection의 순서에 따라 값이 바뀔 가능성이 있습니다. 즉, 데이터 일관성 문제가 발생할 수 있습니다.

→ 이러한 문제를 해결하기 위한 방안 중 하나가 `Lock`으로 Connection A가 Data 접근할 경우 자물쇠를 걸어 Connection B, C, D의 접근을 제어하고 데이터 일관성을 유지하는 매커니즘입니다.

![Untitled](https://github.com/junhong625/TIL/assets/83000975/42c904f5-a801-40c1-a03f-57c55d0bd0da)

<br>

# JPA에서의 Lock

위와 같이 요청이 많은 서버에서는 여러 트랜잭션이 동시에 같은 데이터를 업데이트 하려는 현상으로 인해 일부 요청이 유실되고 장애로 이어질 수 있습니다.

그만큼 데이터베이스에 대한 **동시 액세스(concurrency)**를 적절하게 관리하는 것이 중요합니다.

이에 대한 방안으로 JPA에서는 `낙관적 잠금(Optimistic Lock)`과 `비관적 잠금(Pessimistic Lock)`을 통해 동시 액세스를 적절히 관리할 수 있습니다.

<br>

## JPA의 낙관적 잠금(Optimistic Lock)

> 데이터 갱신시 충돌이 발생하지 않을 것이라고 낙관적으로 보고 잠금을 거는 기법입니다. DB 트랜잭션을 이용하지 않고 어플리케이션 레벨에서 지원하는 락으로, 이는 충돌 감지(Conflict detection)에 가깝다고 볼 수 있습니다.
> 

<br>

### 낙관적 잠금은 언제 사용하는 것이 좋을까?

**낙관적 잠금**은 충돌을 예방하기 위한 로직이 있는 **비관적 잠금**보다 성능이 좋습니다. 하지만 충돌 시 Rollback이 일어나는데 개발자가 수동 Rollback 처리를 해줘야한다는 단점이 있습니다. 

→ 그렇기에 충돌이 빈번하게 발생하지 않는 경우에 낙관적 잠금을 사용하는 것이 좋습니다.

<br>

## 낙관적 잠금 사용 방법

### `@Version`

> JPA에서 사용하는 낙관적 잠금 매커니즘은 `version`이라는 속성을 통해 Entity의 변경사항을 감지하는 방식입니다.
> 

`@Version` annotation을 통해 간단하게 구현이 가능합니다.

JPA는 Select 시에 트랜잭션 내부 version 속성의 값을 보유하고 트랜잭션이 업데이트를 하기 전에 버전 속성을 다시 확인합니다. 그 동안에 version 정보가 변경이 되었다면 트랜잭션은 적용되지 않고 version 속성을 증가하는 업데이트를 하게 됩니다.

<br>

### 주의사항

- 각 Entity 클래스에는 하나의 version만 있어야 합니다.
- 여러 테이블에 매핑 된 Entity의 경우 기본 테이블에 배치되어야 합니다.
- version에 명시할 타입은 `int`, `Integer`, `long`, `Long`, `short`, `Short`, `java.sql.Timestamp` 중 하나 여야 합니다.

<aside>
💡 version에 명시할 타입이 자동으로 지원하는 타입이 아닐 경우 발생하는 에러에 대한 해결책

`org.hibernate.type.VersionType`을 상속받아 seed(초기값), next(증가하는 로직), getComparator(version 비교 함수)를 구현해 커스텀해주면 에러를 해결하고 원하는 타입으로 사용 가능합니다.

</aside>

<br>

### 사용 방법

특정 필드에 `@Version` annotation을 추가하면 자동적으로 낙관적 잠금이 적용됩니다.

```java
@Entity
public class Member implements Serializable {

	@Id
	@GeneratedValue(strategy = GenerationType.AUTO)
	private Long memberNo;

	@Version
	private int version;

	// ...
```

실제로 쿼리를 실행해보면 업데이트 쿼리 발행시에 조건절에 버전정보가 설정된 것을 확인할 수 있습니다. 조건 절에서 비교 후 version이 맞다면 update 시에는 +1된 값이 version에 적용될 것이고, 이미 버전 정보가 바뀐 상태라면 충돌 감지를 통해 예외(`OptimisticLockException`)가 발생하게 됩니다.

![Untitled](https://github.com/junhong625/TIL/assets/83000975/f28308ac-a7b7-4cf5-8c04-b416cb2b339f)

<aside>
💡 `OptimisticLockException`

해당 에러가 발생하게 되면 트랜잭션은 롤백 처리를 진행하게 됩니다.

</aside>

<br>

## 낙관적 락의 LockModeType

LockModeType을 통해 Lock Option을 변경할 수 있습니다.

**None**

> 별도의 옵션을 사용하지 않아도 Entity에 @Version이 적용된 필드만 있으면 낙관적 잠금이 적용됩니다.
> 
- 조회한 Entity를 수정하는 시점에 다른 트랜잭션으로부터 **변경(또는 삭제)되지 않음을 보장**합니다.

<br>

**OPTIMISTIC (Read)**

> Entity 수정시에만 발생하는 낙관적 잠금이 **읽기 시에도 발생**하도록 설정합니다.
> 
- 읽기시에도 버전을 체크하고 트랜잭션이 종료될 때까지 다른 트랜잭션에서 변경하지 않음을 보장합니다. 이를 통해 `dirty read`와 `non-repeatable read`를 방지합니다.

<aside>
💡 `dirty read` : 다른 트랜잭션에 의해 수정됐지만 아직 커밋되지 않은 데이터를 읽는 것을 말합니다.
`non-repeatable read` : 한 트랜잭션 내에서 반복 읽기를 수행하면 다른 트랜잭션의 커밋 여부에 따라 조회 결과가 달라지는 문제입니다.

</aside>

<br>

**OPTIMISTIC_FORCE_INCREMENT (Write)**

> Entity가 물리적으로 변경되지 않았지만, 논리적으로 변경되었을 경우 버전을 증가하고 싶을 때 사용합니다.
> 
- entity가 직접적으로 수정되지 않았어도, 트랜잭션을 커밋할 때 UPDATE 쿼리를 사용해 강제로 version을 증가시킵니다.

<br>

**READ, WRITE**

> `READ` 는 `OPTIMISTIC`과 같은 역할을 하고, `WRITE` 는 `OPTIMISTIC_FORCE_INCREMENT`와 같은 역할을 합니다.
> 

---

### 참조
- [[10분 테코톡] 우르의 Lock & JPA Lock](https://www.youtube.com/watch?v=LDi5muN2kgI&list=PLgXGHBqgT2TvpJ_p9L_yZKPifgdBOzdVH&index=32&ab_channel=우아한테크)
- [JPA의 낙관적 잠금(Optimistic Lock), 비관적 잠금(Pessimistic Lock)](https://velog.io/@lsb156/JPA-Optimistic-Lock-Pessimistic-Lock)
- [[Spring Boot] JPA 동시성 이슈, 낙관적 락(Optimistic Lock)을 이용한 해결](https://chaewsscode.tistory.com/181)
- [JPA 잠금(Lock) 이해하기](https://reiphiel.tistory.com/entry/understanding-jpa-lock)