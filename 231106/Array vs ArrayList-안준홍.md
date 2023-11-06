# Array vs ArrayList
> 둘의 가장 큰 차이점은 **길이를 조정할 수 있냐 없냐**입니다. Array는 고정 길이로 초기화 시 길이를 설정하게 됩니다. 하지만 ArrayList는 가변 길이로, 설정된 Capacity보다 많은 객체들이 들어오게 되면 Capacity를 1.5배로 변경하며 길이를 1.5배 증가시키게 됩니다. 또한 **Array는 원시타입과 참조타입 모두 저장이 가능하지만 ArrayList는 참조타입만 저장 가능**하다는 차이점이 있습니다.

<br>

### Array
- 고정 길이
- 연속된 물리 주소
- Index를 통해 값 참조
- 중복되는 요소를 저장 가능
- Primitive, Object 타입 모두 저장 가능
- Null 값 저장 가능
- 조회 시간 복잡도: O(1)
- 삽입, 삭제 시간 복잡도: O(n)

<br>

### ArrayList
- 가변 길이
- Capcity에 의해 길이가 변화
- 연속된 물리 주소
- Index를 통해 값 참조
- 중복되는 요소 저장 가능
- Object 타입만 저장 가능
- Null 값 저장 가능
- 조회 시간 복잡도: O(1)
- 삽입, 삭제 시간 복잡도: O(n)

<br>

---
### 참조
[[자료구조] Array vs ArrayList](https://velog.io/@humblechoi/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0-Array-vs-ArrayList)  