### group by의 역할에 대해 설명해주세요.

GROUP BY 는 GROUP BY 명령어를 통해 특정 컬럼을 기준으로 연산한 결과를 집계 키로 정의하여 그룹을 짓는 역할을 합니다.

집합 연산자는 COUNT, SUM, AVG, MAX, MIN 등이 있고, DISTINCT와 같이 중복 데이터를 제거하는 특징이 있습니다.

---

- GROUP BY로 그룹화 하지 않은 컬럼은 집계함수를 통해서만 조회하도록 해야 한다.
- GROUP BY는 DISTINCT와 같이 중복 데이터를 제거한다. 집계함수를 사용하여 특정 GROUP으로 분류하고 정렬이 필요하다면 GROUP BY 절을, 특정 그룹 구분없이 단순히 중복 제거가 필요할 경우 DISTINCT를 사용하는 것이 좋다.
- GROUP BY 절에서 조건을 주려면 WHERE이 아닌, HAVING 절을 사용해야 한다.
