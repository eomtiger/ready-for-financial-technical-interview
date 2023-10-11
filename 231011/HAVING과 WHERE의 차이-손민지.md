# HAVING과 WHERE의 차이
having은 그룹화 또는 집계가 발생한 후 그룹을 필터링 하는데 사용되고,  
where은 그룹화 또는 집계가 발생하기 전에 개별 행을 필터링하는데 사용됩니다.

집계 함수(COUNT, SUM, AVG, MAX, MIN 등)는 having절과 함께 사용할 수 있으나,  
where절은 사용할 수 없습니다. (집계함수를 사용할 수 있는 GROUP BY 절보다 WHERE절이 먼저 수행)
<br>
<br>

## 배경 지식
SELECT 쿼리의 수행 순서  
FROM, ON, JOIN > WHERE, GROUP BY, HAVING > SELECT > DISTINCT > ORDER BY > LIMIT

1. FROM  
각 테이블을 확인한다.

2. ON  
JOIN 조건을 확인한다.

3. JOIN  
JOIN이 실행되어 데이터가 SET으로 모아지게 된다.  
서브쿼리도 함께 포함되어 임시 테이블을 만들 수 있게 도와준다.

5. WHERE  
데이터셋을 형성하게 되면 WHERE의 조건이 개별 행에 적용된다.  
WHERE절의 제약 조건은 FROM절로 가져온 테이블에 적용될 수 있다.

6. GROUP BY  
WHERE의 조건 적용 후 나머지 행은 GROUP BY절에 지정된 열의 공통 값을 기준으로 그룹화된다.  
쿼리에 집계 기능이 있는 경우에만 이 기능을 사용해야 한다.

8. HAVING  
GROUP BY절이 쿼리에 있을 경우 HAVING 절의 제약조건이 그룹화된 행에 적용된다.

9. SELECT  
SELECT에 표현된 식이 마지막으로 적용된다.

10. DISTINCT  
표현된 행에서 중복된 행은 삭제

11. ORDER BY  
지정된 데이터를 기준으로 오름차순, 내림차순 지정

12. LIMIT  
LIMIT에서 벗어나는 행들은 제외되어 출력된다.
