### SQL에서 UNION과 UNION ALL의 차이는?

UNION이나 UNION ALL은 둘 다 구조가 같은 데이터 행을 더해서 보여주는 기능을 가지고 있다. 차이점은, **UNION**은 unique한 레코드만 보여주는 반면 **UNION ALL**은 중복 데이터도 같이 보여준다.

---

**UNION**

```sql
SELECT * FROM EMPLOYEE WHERE ID = 5
UNION
SELECT * FROM EMPLOYEE WHERE ID = 5
```

ID 가 5인 사람이 한 명만 있다고 할 때, 위의 쿼리에서는 행이 하나 보여진다.

**UNION ALL**

```sql
SELECT * FROM EMPLOYEE WHERE ID = 5
UNION ALL
SELECT * FROM EMPLOYEE WHERE ID = 5
```

하지만 UNION ALL의 실행 결과로는 똑같은 중복 행이 두 개 나올 거라는 것이다.

UNION ALL 이 중복제거하지 않으므로 UNION 보다 속도가 빠르다.

**MySQL 의 내부적으로 UNION ALL 과 UNION 을 처리하는 과정**

1. 최종 UNION [ALL | DISTINCT] 결과에 적합한 임시 테이블을 메모리 테이블로 생성
2. UNION 또는 UNION DISTINCT 의 경우, 임시 테이블의 모든 컬럼으로 Unique Hash 인덱스 생성
3. 서브쿼리 1 실행 후 결과를 임시 테이블에 복사
4. 서브쿼리 2 실행 후 결과를 임시 테이블에 복사
5. 3, 4번 과정에서 임시 테이블이 특정 사이즈 이상으로 커지면 임시 테이블을 디스크 임시 테이블로 변경
6. 임시 테이블을 읽어서 클라이언트에 결과 전송
7. 임시 테이블 삭제


- UNION 이든지 UNION ALL이든지 사실 그리 좋은 SQL 작성은 아니다.
    
    UNION이 필요하다는 것은 사실 두 엔티티(테이블)가 하나의 엔터티(테이블)로 통합이 돼야 했을 엔터티들이었는데, 알 수 없는 이유로 분리 운영되는 경우가 상당히 많다.
    
    즉, 모델링 차원에서 엔터티를 적절히 통합하여 UNION의 요건을 모두 제거하자.
    
- 두 집합에 절대 중복된 튜플(레코드)가 발생할 수 없다는 보장이 있다면 UNION ALL을 꼭 사용하자. (두 집합에서 모두 각각의 PK를 조회하는데, 그 두 집합의 PK가 절대 중복되지 않는 형태)
- 중복이 있다 하더라도 그리 문제 되지 않는다면 UNION 보다는 UNION ALL을 사용하자.
- 만약 UNION이나 UNION ALL을 사용해야 한다면, 최소 필요 컬럼만 SELECT 하자.
