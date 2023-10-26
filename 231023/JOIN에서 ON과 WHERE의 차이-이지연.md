### JOIN에서 ON과 WHERE의 차이를 설명해주세요.

**ON** 이 WHERE 보다 먼저 실행되어 JOIN 을 하기 전에 필터링을 하고 (=ON 조건으로 필터링이 된 레코들간 JOIN이 이뤄진다)

**WHERE** 은 JOIN 을 한 후에 필터링을 합니다. (=JOIN을 한 결과에서 WHERE 조건절로 필터링이 이뤄진다)

---

- **INNER JOIN**시 ON과 WHERE의 퍼포먼스 차이는 없다.
    - 그렇지만 가독성이 더 좋고, OUTER JOING으로 수정이 용이하다는 점에서 ON을 쓰자.
- **OUTER JOIN**에서의 ON과 WHERE
    - ON으로 해야 원하는 결과를 얻을 수 있다.
    
    table 1:
    
    | co1 | co2 |
    | --- | --- |
    | 1 | 하나 |
    | 2 | 둘 |
    | 3 | 셋 |
    
    table 2:
    
    | co1 | co2 |
    | --- | --- |
    | 1 | 일 |
    | 2 | 이 |
    - **ON**
        
        ```sql
        SELECT t1.col1, t1.col2, t2.col1, t2.col2
        FROM   table1 t1
        LEFT OUTER JOIN table2 t2
        ON t1.col1 = t2.col1
        AND t2.col2 = '일';
        ```
        
        | t1.col1 | t1.col2 | t2.col1 | t2.col2 |
        | --- | --- | --- | --- |
        | 1 | 하나 | 1 | 일 |
        | 2 | 둘 | null | null |
        | 3 | 셋 | null | null |
    - **WHERE**
        
        ```sql
        select t1.col1, t1.col2, t2.col1, t2.col2
        from  table1 t1
        LEFT OUTER JOIN table2 t2
        ON t1.col1 = t2.col1
        where t2.col2 = '일';
        ```
        
        | t1.col1 | t1.col2 | t2.col1 | t2.col2 |
        | --- | --- | --- | --- |
        | 1 | 하나 | 1 | 일 |
