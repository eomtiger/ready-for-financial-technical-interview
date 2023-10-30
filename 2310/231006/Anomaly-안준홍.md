# Anomaly(이상현상)
DB에서 정규화를 하지 않으면 발생하는 현상으로 삽입이상, 갱신이상, 삭제이상과 같은 현상이 나타날 수 있습니다.

<br>

### 삽입 이상(Insertion Anomaly)
> 특정 데이터가 존재하지 않아 중요한 데이터베이스에 삽입할 수 없을 때 발생합니다.

### 갱신 이상(Update Anomaly)
> 테이블의 특정 데이터를 업데이트 했는데 정상적으로 변경되지 않은 경우, 그리고 너무 많은 행을 업데이트 하는 것을 말합니다.

### 삭제 이상(Deletion Anomaly)
> 특정 정보를 삭제하면, 원치 않는 정보도 삭제되는 현상을 말합니다.

<br>

---
### 참조
- https://developer-talk.tistory.com/256
- https://github.com/gyoogle/tech-interview-for-developer/blob/master/Computer%20Science/Database/%5BDB%5D%20Anomaly.md